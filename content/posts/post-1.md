---
title: "Example post"
date: 2022-01-28T03:00:00+03:00
image: "images/duckpond-small.png"
---

What you need to do is:
1. Create the sockets.
2. Add the sockets to the set (`FD_SET`).
3. Find the socket with the highest file descriptor for calls to select().

Above also works with different type sockets (e.g. `AF_INET`, `AF_INET6`). It even works if you have different type sockets (e.g. one IPv4 and one IPv6) listening on the same port number. Dual stack sockets are a thing but this approach is more flexible.

## Create sockets
For this example I will be creating two sockets. One of them will have an IPv4 address and the other IPv6. Nothing out of the ordinary here.

```C
	/* Create IPv4 socket */
	struct sockaddr_in serv_addr4, cli_addr4;
	int addrlen4 = sizeof(cli_addr4);

	if ((sockfd_v4 = socket(AF_INET, SOCK_STREAM, 0)) == -1) {
		perror("socket");
		return 1;
	}

	setsockopt(sockfd_v4, SOL_SOCKET, SO_REUSEADDR, &option, sizeof(int));

	serv_addr4.sin_family = AF_INET;
	serv_addr4.sin_addr.s_addr = inet_addr(IPV4_ADDR);
	serv_addr4.sin_port = htons(IPV4_PORT);

	if (bind(sockfd_v4, (struct sockaddr *)&serv_addr4, sizeof(serv_addr4)) < 0) {
		perror("bind");
		return 1;
	}

	if (listen(sockfd_v4, BACKLOG) < 0) {
		perror("listen");
		return 1;
	}

	/* Create IPv6 socket */
	struct sockaddr_in6 serv_addr6, cli_addr6;
	int addrlen6 = sizeof(cli_addr6);

	if ((sockfd_v6 = socket(AF_INET6, SOCK_STREAM, 0)) == -1) {
		perror("socket");
		return 1;
	}

	setsockopt(sockfd_v6, SOL_SOCKET, SO_REUSEADDR, &option, sizeof(int));
	serv_addr6.sin6_family = AF_INET6;
	inet_pton(AF_INET6, IPV6_ADDR, &serv_addr6.sin6_addr);
	serv_addr6.sin6_port = htons(IPV6_PORT);

	if (bind(sockfd_v6, (struct sockaddr *)&serv_addr6, sizeof(serv_addr6)) < 0) {
		perror("bind");
		return 1;
	}

	if (listen(sockfd_v6, BACKLOG) < 0) {
		perror("listen");
		return 1;
	}

```

## Adding sockets to the set and calling select()
`FD_SET()` is called on each socket. Later on we compare the two sockets to see which one has the highest file descriptor (stored in `maxfd`). Additionally, there's an array of structures that also contain sockets (`clients`), their values are also checked to find the highest descriptor. Finally we can call `select()` with `maxfd + 1`.
```C
	for (;;) {
		FD_ZERO(&descriptors);
		FD_SET(sockfd_v4, &descriptors);
		FD_SET(sockfd_v6, &descriptors);
		if (sockfd_v6 > sockfd_v4)
			maxfd = sockfd_v6;
		else
			maxfd = sockfd_v4;
		/* Add all socket descriptors to the read list. */
		for (id = 0; id < maxclients; id++) {
			if (clients[id] != NULL) {
				FD_SET(clients[id]->connfd, &descriptors);
				/* Find highest file descriptor, needed for the select function. */
				if (clients[id]->connfd > maxfd)
					maxfd = clients[id]->connfd;
			}
		}

		if (select(maxfd + 1 ,&descriptors, NULL, NULL, NULL) == -1)
			perror("select");
...
```

## Full server example
The snippets in this post are taken from kernal-chat and simplified. You can find the full source code [here](https://gitlab.com/kernal/kchat/-/blob/master/src/kchat.c).

Leave us a message on
```
$ nc 2a02:c207:2043:4492:: 1337 # or
$ nc chat.kernal.eu 1337
```

