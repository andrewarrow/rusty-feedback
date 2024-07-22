# rusty_feedback

This is the web framework you use when it's your choice. This is a
web framework that makes it fun and easy to throw together anything
web related.

It's an opinionated framework.

We use full page refreshes by default. When frontend work is required we do that on a per page basis and it becomes an SPA.

We use 

```
cargo install wasm-pack
```

to write all frontend logic still in rust. The frontend and the backend are rust.

We use .mu templates which look like:

```
div p-0 
  {{ template "navbar" . }}
  div flex justify-between
    ul menu bg-base-200 menu-horizontal rounded-box
      li
        a href=./{{$guid}}
          Services
  div flex justify-center mt-3 p-3
    div text-4xl
      {{ .name }}
```

It's just HTML but without having to close any tags (two spaces indent to show which tag is under another.) all the words after the tag are made classes. No need to type class="" and this all gets rendered to normal .html files with rust templates.

```
[dependencies]
tera = "1.13"
serde = { version = "1.0", features = ["derive"] }
```

tera is the way. We use the same template in the backend and frontend. wasm-pack will use tera and render what might be called server-side templates client side.


[https://tailwindcss.com/](https://tailwindcss.com/) and [https://daisyui.com/](https://daisyui.com/) is how we make everything look polished and professional.


