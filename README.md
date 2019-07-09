# Blog set up with `Hugo` and hosted on `Netlify`.

[Blog post on how to set up Hugo and Netlify](https://blog.tomosewe.com/posts/setting-up-a-blog-with-hugo-and-netlify/)

[Install Hugo](https://gohugo.io/getting-started/installing)

``` bash
brew install hugo
```

Make sure you git clone the theme every time you clone this repository, otherwise it will serve nothing.

``` bash
cd themes/
git clone https://github.com/spf13/hyde.git
```

Build all files:

``` bash
hugo
```

Run the server:
``` bash
hugo server -D
```
