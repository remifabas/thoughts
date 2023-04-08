# How to recreate this book

## Install rust

[rust install documentation](https://www.rust-lang.org/tools/install)

## Install mdbook with cargo

[mdbook install documentation](https://rust-lang.github.io/mdBook/guide/installation.html)

## Activate Github actions

In your github repository, go to settings, pages.
select : Deploy from branch, <your_branch>, and docs folder

## Build current markdown to Html

You can use some makefile targets to:

- locally serve the book

```
make serve
```

- build html/js in docs folder

```
make build
```
