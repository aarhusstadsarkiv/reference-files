## reference files
Generic json-files used by more than one repository.

**DO NOT** edit the json-files directly in the browser. Syntax errors are bound to occur.

### to_reidentify.json
This file lists all Pronom-identification formats that we regard as misplaced. Usually due to matching on extension only. All files identified as one of these formats, are to reidentified against our own identifiers in custom_signatures.json.

### custom_signatures.json
This file lists all our own custom-identifiers. These are additions or corrections to the identifiers in the Pronom Registry.

### to_extract.json
This file lists all Pronom- and custom-identified file formats that `unarchiver`can extract.

### to_ignore.json
This file lists all Pronom- and custom-identified file formats that we currently ignore. Usually due to the format not being worthy of preservation.

### to_convert.json
This file lists all Pronom-identified file formats that we can and wish to convert to an archival master format. Each entry has the following structure:

```json
"{format_id}": {
    "name": "{signature or the format}",
    "master_converter": "{name of converter to use}",
    "master_format": [
        "{list of master formats to generate}"
    ],
    "statutory_converter": "{name of statutory converter to use}",
    "statutory_format": [
        "{list of statutory formats to generate}"
    ]
}
```

For example:

```json
"fmt/1451": {
    "name": "PDF Portfolio 1.7",
    "master_converter": "pdf",
    "master_format": [
        "pdf"
    ],
    "statutory_converter": "gs",
    "statutory_format": [
        "tif"
    ]
}
```
#### Notes
- 'master_converter' is the name of the converter that `convertool` should use to convert to the requested 'master_format'.
- 'master_format' can contain more than one format. This usually happens if `convertool's` `statutory-converter` needs a different format from the primary master format to perform its conversion job.
- 'statutory_converter' is only present, if the format is one of those used by `statutory_converter` to convert to the statutory archival formats.
- 'statutory_format' determines the file format that `statutory_converter` will save to (tif, wav, gml...). It is a list, but for now it only contains one format.
- It as not always that Ghostscript (`convertool's pdf_converter`) is able to convert the many different pdf formats to PDF/A. But as it converts ALL pdf formats to tif, all pdf-entries contains a `statutory_`-keys that signals to the `statutory_converter` that it should convert the format.
