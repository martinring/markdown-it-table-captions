# markdown-it-table-captions

> Table caption plugin for [markdown-it](https://github.com/markdown-it/markdown-it) markdown parser.

## Syntax

Syntax based on Pandoc [`table_captions`](https://pandoc.org/MANUAL.html#extension-table_captions). Should work with other table extension.

Paragraph starting with `Table:` or `:` immediately before or after a table is interpreted as a caption. E.g:

````markdown
Table: A Caption

| A | B |
|---|---|
| 1 | 2 |
````

or 

````markdown
| A | B |
|---|---|
| 1 | 2 |

Table: A Caption
````

or

````markdown
| A | B |
|---|---|
| 1 | 2 |

: A Caption
````

all result in

````html
<table>
  <caption>A Caption</caption>
  <thead>
    <tr>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
````

> Note that unfortunately pandoc gfm tables behave differently from markdown-it gfm tables such that in markdown-it a blank line has to be between the table and a subsequent caption, because otherwise the caption is interpreted as part of the table.

## Use

````js
import md from 'markdown-it'
import table_captions from 'markdown-it-table-captions'

const markdown = md().use(table_captions)

markdown.render('...')
````
