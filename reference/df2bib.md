# Export a BibTeX `tibble` to a .bib file

The BibTeX `tibble` is written to a .bib file

## Usage

``` r
df2bib(x, file = "", append = FALSE, allfields = TRUE)
```

## Arguments

- x:

  `tibble`, in the format as returned by
  [`bib2df`](https://docs.ropensci.org/bib2df/reference/bib2df.md).

- file:

  character, file path to write the .bib file. An empty character string
  writes to `stdout` (default).

- append:

  logical, if `TRUE` the `tibble` will be appended to an existing file.

- allfields:

  logical, if `TRUE` (default), the resulting bib output will include
  all the BibTeX fields contained in the df object. If `FALSE` only the
  fields with text will be included in the resulting bib object

## Value

`file` as a character string, invisibly.

## References

<https://www.bibtex.org/Format/>

## See also

[`bib2df`](https://docs.ropensci.org/bib2df/reference/bib2df.md)

## Author

Thomas J. Leeper

Gianluca Baio

## Examples

``` r
# Read from .bib file:
path <- system.file("extdata", "bib2df_testfile_3.bib", package = "bib2df")
bib <- bib2df(path)

# Write to .bib file:
# bibFile <- tempfile()
# df2bib(bib, bibFile)

# Use `append = TRUE` to add lines to an existing .bib file:
# df2bib(bib, bibFile, append = TRUE)
```
