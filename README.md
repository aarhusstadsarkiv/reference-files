## reference files
Generic json-files used by more than one repository.

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

### to_convert_unarchiver.json
This file is not currently used. Unarchiver keeps its own list of "unarchivable" formats in "constants.py"
