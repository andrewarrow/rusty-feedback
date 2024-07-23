# rusty-feedback

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

It's just HTML but without having to close any tags (two spaces indent to show which tag is under another.) all the words after the tag are made classes. No need to type class="".
No need to use quotes but you can't have spaces.

This all gets rendered to normal .html files with rust templates.

```
[dependencies]
tera = "1.13"
serde = { version = "1.0", features = ["derive"] }
```

tera is the way. We use the same template in the backend and frontend. wasm-pack will use tera and render what might be called server-side templates client side.


[https://tailwindcss.com/](https://tailwindcss.com/) and [https://daisyui.com/](https://daisyui.com/) is how we make everything look polished and professional.

[https://www.postgresql.org/](https://www.postgresql.org/) and [https://www.sqlite.org/](https://www.sqlite.org/) are the database we support.


```
    use std::collections::HashMap;

    let rows = client.query("SELECT * FROM users", &[]).await?;

    // Iterate over the rows and create dictionaries
    let mut results = Vec::new();
    for row in rows {
        let mut row_dict = HashMap::new();
        for (i, column) in row.columns().iter().enumerate() {
            let column_name = column.name();
            let value: Option<String> = row.try_get(i).unwrap_or(None);
            row_dict.insert(column_name.to_string(), value);
        }
        results.push(row_dict);
    }
```

This is all you get in terms of an ORM.

We don't strongly type things. We just use these HashMap everywhere for dealing
with data.

This repo is based off the golang version called just:

[https://github.com/andrewarrow/feedback/](https://github.com/andrewarrow/feedback/)

it has all these features above but in go vs rust.

I'm slowly moving everything from go to rust and want to market this framework as rusty-feedback.

The name feedback comes from the coding style. Everything is very messy and in flux think saw-dust-on-the-floor construction site. As in, look at this function, see what it's doing? What do you think? Any feedback?

And because you are shown the code with that frame of mind, here's a start of what I'm thinking, do you see the vision? I know it's not perfect, by all means, give me feedback. 


