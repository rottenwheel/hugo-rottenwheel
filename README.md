# rottenblog

This is the source code for [rottenblog](https://blog.rottenwheel.com/). It is a static site generated using [Hugo](https://gohugo.io/).

[Rottentheme](https://github.com/rottenwheel/rottentheme) is the theme used by rottenblog.

## Getting Started

### Prerequisites

- [Hugo](https://gohugo.io/getting-started/installing/) installed on your machine.

### Installation

1. Clone the repository:

   ```sh
   git clone https://github.com/rottenwheel/hugo-rottenwheel.git
   cd hugo-rottenwheel
   ```

2. Run the Hugo server:

   ```sh
   hugo server
   ```

3. Open your browser and visit `http://localhost:1313` to see the site.

### Deployment

If you use GitHub, this repository comes with a GitHub Actions workflow that automatically builds and deploys the site to the `pages` branch whenever you push changes to the `main` branch.

Otherwise, you can build the site manually:

```sh
hugo --minify
```

The generated site will be in the `public/` directory.

## Adding a New Post

1. Create a new Markdown file in the `content/posts/` directory:

   ```sh
   hugo new posts/my-new-post.md
   ```

2. Edit the new post file to add your content.

   ```markdown
   ---
   title: "My New Post"
   date: 2024-07-15
   ---

   # My New Post

   This is the content of my new post.
   ```

3. Save the file and refresh your browser to see the new post.

## Customizing the Homepage

The homepage content and layout can be customized by editing the `content/_index.md` file and the `layouts/index.html` template.

- `content/_index.md`: Contains the metadata for the homepage.
- `layouts/index.html`: Defines the HTML structure and layout for the homepage.

## License

Hugo Rottenwheel is released under GNU General Public License v3.0. See [LICENSE](./LICENSE) for more information.
