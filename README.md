# MD Static Site Generator 🚀

This project is a simple yet powerful static site generator for building personal websites. It dynamically converts Markdown files into HTML, uses templates for rendering, and supports GitHub Pages for deployment.

## Features

| Feature                              | Description                                                                   |
| ------------------------------------ | ----------------------------------------------------------------------------- |
| Markdown File Support                | Easily create and manage your content in Markdown format.                     |
| Category-Based Listing               | Automatically generates separate listing pages for blog and book content.     |
| Template-Based HTML Rendering        | Uses [Tera](https://tera.netlify.app/) template engine to render HTML pages.  |
| Dynamic Content Structure            | Automatically scans content files and creates the site structure accordingly. |
| Static Asset Management              | Copies all static files from the `assets` folder to the target directory.     |
| GitHub Actions for CI/CD Integration | Automates deployment and supports continuous integration with GitHub Actions. |

## Usage

### Prerequisites

- **Rust**: The project requires Rust for execution. Install it using [Rust Installer](https://www.rust-lang.org/tools/install).

### Installation

1. Clone the repository:

```sh
git clone https://github.com/mumudevx/personal-website.git
cd personal-website
```

2. Build the project:

```sh
  cargo build
```

3. Prepare your content structure as follows:

```
src/
  content/
    blog/
      my-blog-post.md
    book/
      my-favorite-book.md
  assets/
    image.png
  template/
    base.html
    blog_list.html
    book_list.html
    homepage.html
```

4. Generate the static site:

```sh
cargo run
```

5. The output will be available in the dist/ directory.

## GitHub Actions Integration

The project includes CI/CD integration with GitHub Actions, enabling automatic deployment to GitHub Pages.

### Steps

1. Configure GitHub Pages:

- Go to your GitHub repository.
- Navigate to Settings > Pages.
- Set the Source to the gh-pages branch.
- Create a GitHub Actions workflow file: .github/workflows/deploy.yml

2. Create a GitHub Actions workflow file: `.github/workflows/deploy.yml`

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Setup Rust
        uses: actions-rs/toolchain@v1
        with:
          toolchain: stable

      - name: Build static site
        run: cargo run

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

3. Push your changes to the main branch. GitHub Actions will automatically build and deploy the site to GitHub Pages.

<br>

# Project Features

## Content and Templating

Place your Markdown files in the following structure:

```
src/
  content/
    blog/
      post1.md
    book/
      book1.md
  template/
    base.html
    homepage.html
    blog_list.html
    book_list.html
```

## Output

After running the command, the dist/ directory will contain the following output structure:

```
dist/
  index.html
  blog.html
  book.html
  blog/
    post1.html
  book/
    book1.html
  assets/
    image.png
```

# Notes

- You can include metadata at the beginning of your Markdown files, for example:

```markdown
---
title: "Blog Title"
---
```

- The metadata is automatically extracted and used for generating listing pages.

<br>

For more information, feel free to check the [issues](https://github.com/mumudevx/md-static-site-generator/issues) section or submit a pull request!
