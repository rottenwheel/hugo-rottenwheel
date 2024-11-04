---
title: 'As Easy as P, G, P'
date: 2024-11-04T16:14:59-06:00
image: "/images/2.jpg"
---

*Turn your Twitter DM's from a honeypot of data just waiting to be exposed into an encrypted jumble of characters that @jack can't simply crack.*
**Note**: This tutorial was written by Diverter_NoKYC, not me; I am simply offering a clearnet and .onion mirror since original site is down.

# PGP Encryption Made Simple

**For many users, PGP encryption has been out of reach for some time.**

Use of command line tools are frightening to many, and so often times the task of encrypting data has been forwarded on to a third party provider in the form of end-to-end encrypted messaging platforms like Signal or Threema. With data that one considers truly sensitive though, trusted third parties are most certainly security holes. For cases such as these, we need encryption made as simple as possible. Enter [OpenKeychain](https://web.archive.org/web/20230208170414/https://openkeychain.org/).

![OpenKeychain](/images/openkeychain.png)

### So Easy I Can Do It

OpenKeychain is a mobile app available for download to Android users in either the Play Store or [F-Droid](https://web.archive.org/web/20230208170414/https://f-droid.org/en/packages/org.sufficientlysecure.keychain/). It is an exceedingly simple tool, but just to be sure I am going to go over getting started with this tiny, yet powerful tool for privacy and security. Upon download, you will be met with a screen offering you the chance to `Create My Key`.

![OpenKeychain_create](/images/openkeychain1.png)

Make that selection, and you will next be asked to provide information to associate with this particular PGP key. This part is important, as you will need to make a decision beforehand whether this will be a key you will be associating with your identity or your nym and sharing around social media, or if this key is just for you to deal with highly personal or sensitive information and will need to be kept to yourself.

![OpenKeychain_manage](/images/openkeychain2.png)

Make your decision, and fill in this information accordingly. The same goes for the next section, which asks for your email address to be associated with this key. Similarly, realize this email address will be tied to this key, and thus to the name you associate with the same key. If publicly sharing for others to contact you in a more private, secure way, you may want to go ahead and include your personal email you would prefer them to contact. If not, fill in with whatever silly information you like.

![OpenKeychain_manage1](/images/openkeychain3.png)

Once that is complete you will be presented with an overview of the information you have entered, as well as given the option to publish this key on keyservers. You will notice the ability to finish and create your PGP key now. But not so fast--)

![OpenKeychain_threedots](/images/openkeychain4.png)

Before we do that, let us take a look at the actual key configuration and decide on any changes that we would like to make. Select the menu by pressing the 3 dots in the top right corner. You will see a popup offering the ability to Change Key Configuration. Select that button, and let's take a look.

### How You (Con)Figure That?

On the key configuration screen, you will see the name and email address given earlier toward the top, and toward the bottom you should see two default subkeys showing `RSA, 3072` bit as the description.

![RSA3072](/images/3072.png)

Let's select that first subkey and make it just a bit stronger to be on the safe side. When you select the first subkey, you will be presented with several options for the functionality of the key, as well as a drop down menu toward the top to deal with the type and strength of encryption.

![Change-RSA3072](/images/change3072.png)

Select the drop down menu first. You will see several options available, but not to worry. We will be sticking with the RSA keys here, we just want to buff it up a little more from 3072 bit to the `RSA 4096` option.

![RSA-4096](/images/4096.png)

You can see generic descriptions of timeframes these keys are expected to be considered secure alongside each option. RSA 1024 keys have been broken and insecure for some time now, and I am of the opinion that we will see RSA 2048 keys be broken within the next 5-10 years. Note, I could be completely wrong, it may take 1 year, it may take another 20, though I doubt it. Point being, this does not scale linearly. So even if RSA 2048 is broken 2 years from now, this does not mean RSA 3072 is then insecure, or even that it will likely be broken within another 2 years. The main point though is since RSA 4096 is right here for us to select, we might as well go ahead and take it, just to be sure. I am not going to spend time on the ECC keys, but if you like you can look into them [here](https://web.archive.org/web/20230208170414/https://en.wikipedia.org/wiki/Elliptic-curve_cryptography). Select `RSA 4096` and let's move on. Next is the key functionality. This particular subkey will be used for signing messages. Select `Sign` from the menu options next, then select `OK`.

![sign](/images/sign.png)

### Finish Him

Now you will be returned to the key configuration page, and should see your information as well as two subkeys, one marked with `RSA, 4096` bit and one marked with `RSA, 3072` bit. Select the second, the `RSA, 3072` bit subkey and you will notice it disappears.

![disappears](/images/disappears.jpg)

Not to worry, simply select `Add Subkey` and we will replace it with an even stronger one. Repeat the process done with the previous subkey by selecting `RSA 4096` from the drop down menu. This time though, instead of signing, this key will be doing the encrypting of messages. Select `Encrypt` from the menu options, and then `OK`.

![encrypt](/images/encrypt.jpg)

Once that is done, ensure your name and email information appear correctly on the configuration page. You should see two subkeys at the bottom just like when we began this process, only now they should both read `RSA, 4096` bit in the description. If all this is correct, select the Save button in the top right corner, and you will be returned to the key creation page. To publish or not to publish, that is the question. We are back to deciding whether this key will be uploaded to keyservers. Now [keyservers](https://web.archive.org/web/20230208170414/https://en.wikipedia.org/wiki/Key_server_(cryptographic)) are essentially big, public rolodexes of public PGP keys uploaded by users for querying. This can be done using the [fingerprint](https://web.archive.org/web/20230208170414/https://en.wikipedia.org/wiki/Public_key_fingerprint) or other information on sites such as the [Ubuntu Keyserver](https://web.archive.org/web/20230208170414/https://keyserver.ubuntu.com/) or various others. My general rule of thumb at this point is to default to **not** uploading your key at this time. The reason is quite simple: you can always go back and upload to keyservers at any time. It is a much different thing to upload a key and then wish it weren't public.

![create](/images/create.png)

So let's leave that box `unchecked` and instead select `Create Key` in the bottom right hand corner.

### Encryption Is The Key

It may take a few moments to generate the key, it may not. Depends on the device you are using for this endeavor. Regardless, when finished you will see your key listed then on the keys page.

![testy](/images/testy.png)

A quick selection of the shown key will reveal some details about the key you just made, though we won't go into too much of that right now. What we mainly want to do is click on your key and look at the section dealing with the key "health". There should be a box with a green check saying `Healthy`, that there are no key issues found. Click that box to expand it.

![healthy](/images/healthy.png)

You will see now the functional ability of your key to confirm other keys, sign messages, and decrypt messages. It is all green and good to go from here. Congratulations! You have created a properly strong RSA 4096 PGP key and are ready to start encrypting!

### Good Thing I'm Bonafide

Let's say you have been interacting with [Bitcoin Q+A](https://web.archive.org/web/20230208170414/https://twitter.com/BitcoinQ_A) on Twitter or Matrix, as well as getting information from his great site, [https://bitcoiner.guide](https://web.archive.org/web/20230208170414/https://bitcoiner.guide/). Wouldn't it be nice to have some sort of extra verification that the same person you are speaking with is the one in charge of the bitcoiner.guide site? Let's see what we can do. First, let's get his public PGP key, which he has graciously provided at [https://bitcoiner.guide/pgp](https://web.archive.org/web/20230205073303/https://bitcoiner.guide/pgp/).

![QAPGP](/images/qnapgp.png)

You will need to long press on mobile then expand the highlighted area to cover the key completely. That means all the way to the beginning of `-----BEGIN PGP PUBLIC KEY BLOCK`, and all the way to the end of `END PGP PUBLIC KEY BLOCK-----`. Once you have that highlighted, copy the selected text and go back into OpenKeychain. In the `Keys` tab of the app, select the `+` fast action button on the bottom right of the screen, and then choose `Import From File`.

![Import-file](/images/importfile.png)

The next screen will have nothing to show, but what you need is instead in the menu within the 3 dots in the top right corner. Select those 3 dots and you will be presented with a popup which says `Read From Clipboard`. We know Bitcoin Q+A's key is in our clipboard, so select that button and you should be presented with his key and the opportunity to import it into your keyring.

![Import-key](/images/importk.png)

Select `Import` and there you have it! You now have his public key in your keyring, as well as your own private key. To be safe, you can select Bitcoin Q+A's key from the `Keys` tab in the app, and you should see a page detailing whether or not his key is also marked as "Healthy".

![Not-verified](/images/health.png)

Since everything looks good, we are good to move on to verifying messages that have been signed by Bitcoin Q+A, cryptographically.

### Blue Bot Verified

For that, we need a message from Bitcoin Q+A that he has cryptographically signed using the same key hosted at [https://bitcoiner.guide/pgp](https://web.archive.org/web/20230208170414/https://bitcoiner.guide/pgp). Luckily, I have just that right [here](https://web.archive.org/web/20230208170414/https://matrix.to/#/!DcqRSktqwoymxfZOBb:usethe.tools/$q8t8-3GZ9wdpKKI5JxSKxQnozTphYWXnxbWWuEW3Mck?via=usethe.tools&via=bitcoiner.chat&via=matrix.org) from our Matrix chatroom dedicated to PGP practice, appropriately titled [PGP for Y-O-U](https://web.archive.org/web/20230208170414/https://matrix.to/#/#pgppractice:usethe.tools?via=usethe.tools&via=bitcoiner.chat&via=matrix.org).

![PGP-QNA](/images/pgpqna.png)

All we need to do now is copy this entire message, again all the way from the first `-----BEGIN PGP SIGNED MESSAGE` to the last `END PGP SIGNATURE-----`. Once that has been copied, return again to OpenKeychain. From the `Keys` tab you will select the menu button in the top left corner and then select the `Encrypt/Decrypt` tab.

![PGP-QNA](/images/encrdcr.png)

Inside that tab you will see different options available to encrypt or decrypt messages and files. For our use case here, since we already have the PGP signed message copied on our clipboard, select `Read From Clipboard` from the choices.

![Read-CL](/images/readcl.png)

The app will go through the process of using Bitcoin Q+A's public key you imported and the private key you created for yourself earlier to decrypt and verify the validity of the PGP signature. If it is a good signature, you should see the name associated with the key used to sign the message, in this case Bitcoin Q+A, as well as the actual message.

![Signed](/images/signed.png)

Note that is says `Signed By Unconfirmed Key`. This has confused people in the past into thinking this invalidates the signature, but it does not. This simply means you have not indicated to the OpenKeychain app that you have verified the fingerprint matches the key, essentially saying that you have verified that the owner of this key is actually Bitcoin Q+A. Preferably this would be done in person, like by scanning a QR code, but for our purposes it is not necessary. We have verified that the person that owns the public PGP key posted at [https://bitcoiner.guide/pgp](https://web.archive.org/web/20230208170414/https://bitcoiner.guide/pgp) is the same person in control of the Bitcoin Q+A account on Matrix, and his message is asserting ownership of the key as well. Don't you feel better?

### Encryption, Party of Two

For our final trick, now that our confidence has increased that we are in fact speaking with **the** Bitcoin Q+A, it is time to create an encrypted message that only you and he will be able to decrypt and read. Only you two will have the proper cryptographic key combination to do so, and because of this it enables much more sensitive information to be passed privately over distance using digital communication. The first thing to do is to click on Bitcoin Q+A's key from the `Keys` tab in the app. You will see near the top of the screen a messaging icon with a lock on it.

![Keys](/images/keys.png)

Select that icon and you will be taken to a screen to encrypt a message only the two of you can read. To ensure this, next you will need to select the key you wish to sign and encrypt this message with.

![None](/images/none.png)

If you select the drop down menu here you will see your PGP key as an option to do just that. Select your key, and then begin constructing your private message. **What would you say to Bitcoin Q+A if you knew for sure that only he and you would be able to read what it says?** Let me guess:

![BTCrush](/images/btcrush.png)

Once you have ensured all that information is correct, select the "Share" icon in the top right corner. You should be presented with whatever messaging apps you have installed on your device, or you can just copy it to your clipboard and then paste the message in his Twitter DM's. It will look a little something like this to everyone else:

![PGP-mssg](/images/pgpmssg.png)

### That Wasn't So Hard, Now Was It?

You have now created your own personal PGP key, imported another person's key, verified a PGP signed message, and then encrypted your very own personal message all on mobile using nothing more than copy/paste. This OpenKeychain application makes using PGP easy enough for anyone to do it. You will find yourself scouring the internet for posted public keys of people you interact with so that you can turn your Twitter DM's from a honeypot of data just waiting to be exposed into an encrypted jumble of characters that @jack can't simply crack. For us Android maximalists, there are very few acceptable reasons to not use PGP when needed or necessary, and just one more way to eliminate so much dependency on those security holes known as trusted third parties. For more info or practice feel free to join us in the [Matrix chat](https://web.archive.org/web/20230208170414/https://matrix.to/#/#pgppractice:usethe.tools?via=usethe.tools&via=bitcoiner.chat&via=matrix.org) and drop us some (encrypted) lines!
