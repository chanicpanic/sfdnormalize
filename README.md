# SFD Normalize

Normalize Spline Font Database (SFD) files by discarding GUI state information making them easier to track in version control without clutter and conflicts between users.

This fork optimizes the tool for use with [pre-commit](https://pre-commit.com/)
by accepting multiple files at once and always normalizing the files in place.

It also adds support for the following SFDIR files:

- `font.props`
- `*.glyph`

```console
$ sfdnormalize --help

usage: sfdnormalize [-h] [--version] [--keep KEEP] [--drop DROP] [--sfd-version VERSION] input_files [input_files ...]

Normalize Spline Font Database (SFD) files in place

positional arguments:
  input_files           Input SFD file(s) before normalization

options:
  -h, --help            show this help message and exit
  --version, -V         show program's version number and exit
  --keep, -k KEEP       Keep lines beginning with these even if they'd be normally dropped. (Can provide multiple times.) (default: None)
  --drop, -D DROP       Drop lines beginning with these even if they'd be normally kept. (Can provide multiple times.) (default: None)
  --sfd-version, -s VERSION
                        By default, latest SFD revision known to this program will be written, unless specified here (default: 3.2)

```

## pre-commit

Add the following to your `.pre-commit-config.yaml`:

```yaml
repos:
- repo: https://github.com/chanicpanic/sfdnormalize
  rev: v2.0.0
  hooks:
    - id: sfdnormalize
```
