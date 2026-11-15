# Entry format

Each file in `site/entries/` describes one catalogue item.  The site build reads
the JSON directly, so keep the field names exactly as listed here.

## Common fields

- `slug` -- stable identifier, also used for the page URL
- `title` -- display name
- `kind` -- `tool` or `dataset`
- `status` -- `published`, `accepted` or `archived`
- `channel` -- the track the item was announced in (`core`, `labs`, `edge`)
- `announced` -- ISO date of the announcement
- `summary` -- one-line description used on the index page
- `maintainers` -- list of maintainer names
- `code_url` -- optional; the public source repository of the implementation

## Call-signature block

Tool entries also carry a `parameters` object that describes their call
signature.  The tool pages render it as a reference table:

- `type` -- always `"object"`
- `properties` -- object mapping each argument name to its JSON Schema fragment
- `required` -- array with the names of the arguments that must be supplied

The block is not authored by hand: it is carried over verbatim from the toolbox
export, and the build compares the rendered block with the export copy before
publishing.

Example of the block as rendered by the site:

```json
"parameters": {
  "type": "object",
  "properties": {
    "query": { "type": "string" }
  },
  "required": ["query"]
}
```
