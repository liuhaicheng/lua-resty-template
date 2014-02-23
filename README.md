#lua-resty-template

**lua-resty-template** is a templating engine for OpenResty.

## Hello, World with lua-resty-template

*Lua:*

```lua
local template = require "resty.template"

-- Using template.new
local view = template.new("view.html")
view.message  = "Hello, World!"
view.render()

-- Using template.render
template.render("view.html", { message = "Hello, World!" })
```

*view.html:*

```html
<!DOCTYPE html>
<html>
<body>
  <h1>{{message}}</h1>
</body>
</html>
```

*Output:*

```html
<!DOCTYPE html>
<html>
<body>
  <h1>Hello, World!</h1>
</body>
</html>
```

## Template Syntax

You may use the following tags in templates:

* `{{expression}}`, writes result of expression - html escaped
* `{*expression*}`, writes result of expression 
* `{% lua code %}`, executes Lua code
* `{( template )}`, includes `template` file

## Lua API

`local view = template.new("template.html")`

Creates a new template instance that is used as a context when `render`ed.

Example:

```lua
local template = require "resty.template"
local view = template.new("view.html")
view.message  = "Hello, World!"
view.render()

--You may also pass additional context to render:
view.render({ title = "Testing lua-resty-template" })
```


