# md-static-site-generator
Static site generator feeds from md files to content and routing from folder structure.

## Structure / Sitemap Design

```
src/
  blog/
    my-blog-post-01.md
  book/
    clean-code-bob.md
  assets/
    isolated.png
```

convert to

```
dist/
  blog/
    my-blog-post-01.html
  book/
    clean-code-bob.html
  assets/
    isolated.png

```
