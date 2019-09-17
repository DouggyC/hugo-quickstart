# Hugo CLI commands

>

## Add Some Content

```
hugo new folder/file-name.md
```

### Draft, Future, and Expired Content

Hugo allows you to set draft, publishdate, and even expirydate in your content’s front matter. By default, Hugo will not publish:

> Content with a future `publishdate` value

> Content with `draft: true` status

> Content with a past `expirydate` value

https://gohugo.io/getting-started/usage/

## Hugo does not remove generated files before building

- list pages / single pages
- archetypes
- front matter
- tags
- {{ short codes }}
- taxonomies
- partials
- layouts/\_default/fileName.html

## {{ }} Syntax

.Interpolation

## Hugo Functions

For loop

```
{{ range .Content}}
```

themes/layouts/index.html - home page template

### Section templates

> Section Templates are used to apply individual styling to list content, overriding default theme templates.

layouts/folderName/single.html

### Base template and blocks

>

> layouts/\_default/baseof.html
> layouts/\_default/single.html
> layouts/\_default/list.html

### Variables Interpolation

`Variables only available for use in layouts folder`

> front matter variables

```
{{ .Title }}
{{ .Params.myVar }}
```

> template variable

```
{{ $myVar := "string", 99, boolean }}
{{ $myVar }}
```

### Functions

`Functions only available for use in layouts folder`

```
{{ funcName param1 param2 }}
```

#### Loops

```
{{ range .Pages }}
  {{ .Title }}
{{ end }}
```

### Conditionals

- eq = equal
- lt = less than
- le = less than equal too
- gt = greater than
- ge = greater than equal too
- not = !

---

- else
- with
- or
- and

```
{{ $var1 := 'dog' }}
{{ $var2 := 'cat' }}

{{ if not (eq $var1 $var2) }}
  True
{{ else }}

{{ else if }}
  False
{{ end }}
```

### Data

`Access data`
{{ range .Site.Data.states }}
{{ .name }}
{{ end }}

### Partials Templates

layouts/partials/header.html

```
{{ partial "header" . }}
{{ partial "header" (dist "myTitle" "myCustomTitle" "myDate" "myCustomDate") }}
```

### ShortCode Templates

`Used in content folder`
layouts/shortcodes/myshortcode.html

<p style="color:{{.Get `color`}}">Text</p>
<p style="color:{{.Get 0}}">Text</p>

{{ .Inner }}

in content/page.md

```
{{ < myshortcode color="blue" > }}
  Text
{{ < /myshortcode > }}
```

> Positional Param array index

```
{{ < myshortcode blue > }}
```

```
{{% myshortcode %}}
  **bold text**
{{% /myshortcode %}}
```
