
## reference files
YAML-files containing our collected fileformat info.

**DO NOT** edit the directly in the browser. Syntax errors are bound to occur.

### Editing
When editing the files locally, you can use the following command to check if your edits validate against the relevant schema, e.g. when editing `fileformats.yml`:

`uvx --from check-jsonschema check-jsonschema --verbose --schemafile fileformats.schema.json fileformats.yml`
