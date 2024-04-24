# The ALUMET Books

This repository contains the "Alumet books":

- The [developer book](./developer/), for those who want to extend Alumet with new plugins.
- The [user book](./user/), for the users of the measurement tool, including system administrators who want to deploy it.

The two books are made with [mdBook](https://rust-lang.github.io/mdBook/).

## Generating the books

First, you need to [install mdBook](https://rust-lang.github.io/mdBook/guide/installation.html#installation).

To generate a book, `cd` in its directory, then run `mdbook`.
Example:

```sh
cd user
mdbook serve --open
```

As explained in the [mdBook documentation](https://rust-lang.github.io/mdBook/guide/creating.html#creating-a-book), `serve --open` will build the book, start a local webserver and open the book in your default web browser. Modifying the source of the book will automatically reload the web page.
