# Parse a BibTeX file to a `tibble`

The BibTeX file is read, parsed, tidied and written to a `tibble`

## Usage

``` r
bib2df(file, separate_names = FALSE, merge_lines = FALSE)
```

## Arguments

- file:

  character, path or URL to a .bib file.

- separate_names:

  logical, should authors' and editors' names be separated into first
  and given name?

- merge_lines:

  logical, set to `FALSE` by default. If set to `TRUE` identifies
  entries that span several lines and merges them

## Value

A `tibble`.

## Details

For simplicity `bib2df()` unifies the reading, parsing and tidying of a
BibTeX file while being aware of a standardized output format, different
BibTeX styles and missing values in the BibTeX file.

When `separate_names = TRUE`, the respective columns contain a
`data.frame` for each row. When `FALSE`, the respective columns contain
character strings.

## See also

[`df2bib`](https://docs.ropensci.org/bib2df/reference/df2bib.md)

## Author

Philipp Ottolinger

## Examples

``` r
# Read from .bib file:
path <- system.file("extdata", "bib2df_testfile_3.bib", package = "bib2df")
bib <- bib2df(path)
str(bib)
#> tibble [3 × 26] (S3: tbl_df/tbl/data.frame)
#>  $ CATEGORY    : chr [1:3] "ARTICLE" "BOOK" "INCOLLECTION"
#>  $ BIBTEXKEY   : chr [1:3] "Binmore2008" "Osborne1994" "BrandenburgerDekel1989"
#>  $ ADDRESS     : chr [1:3] NA NA "New York"
#>  $ ANNOTE      : chr [1:3] NA NA NA
#>  $ AUTHOR      :List of 3
#>   ..$ : chr "Binmore, Ken"
#>   ..$ : chr [1:2] "Osborne, Martin J." "Rubinstein, Ariel"
#>   ..$ : chr [1:2] "Brandenburger, Adam" "Dekel, Eddie"
#>  $ BOOKTITLE   : chr [1:3] NA NA "The Economics of Missing Markets, Information and Games"
#>  $ CHAPTER     : chr [1:3] NA NA "3"
#>  $ CROSSREF    : chr [1:3] NA NA NA
#>  $ EDITION     : chr [1:3] NA NA NA
#>  $ EDITOR      :List of 3
#>   ..$ : chr NA
#>   ..$ : chr NA
#>   ..$ : chr "Hahn, Frank"
#>  $ HOWPUBLISHED: chr [1:3] NA NA NA
#>  $ INSTITUTION : chr [1:3] NA NA NA
#>  $ JOURNAL     : chr [1:3] "Topoi" NA NA
#>  $ KEY         : chr [1:3] NA NA NA
#>  $ MONTH       : chr [1:3] NA NA NA
#>  $ NOTE        : chr [1:3] NA NA NA
#>  $ NUMBER      : chr [1:3] "1" NA NA
#>  $ ORGANIZATION: chr [1:3] NA NA NA
#>  $ PAGES       : chr [1:3] "17--27" NA "46--61"
#>  $ PUBLISHER   : chr [1:3] NA "The MIT Press, Cambridge, Massachusetts" "Oxford University Press"
#>  $ SCHOOL      : chr [1:3] NA NA NA
#>  $ SERIES      : chr [1:3] NA NA NA
#>  $ TITLE       : chr [1:3] "Do Conventions Need to Be Common Knowledge?" "A Course in Game Theory" "The Role of Common Knowledge Assumptions in Game Theory"
#>  $ TYPE        : chr [1:3] NA NA NA
#>  $ VOLUME      : chr [1:3] "27" NA NA
#>  $ YEAR        : num [1:3] 2008 1994 1989

# Read from .bib file and separate authors' and editors' names:
bib <- bib2df(path, separate_names = TRUE)
str(bib)
#> tibble [3 × 26] (S3: tbl_df/tbl/data.frame)
#>  $ CATEGORY    : chr [1:3] "ARTICLE" "BOOK" "INCOLLECTION"
#>  $ BIBTEXKEY   : chr [1:3] "Binmore2008" "Osborne1994" "BrandenburgerDekel1989"
#>  $ ADDRESS     : chr [1:3] NA NA "New York"
#>  $ ANNOTE      : chr [1:3] NA NA NA
#>  $ AUTHOR      :List of 3
#>   ..$ :'data.frame': 1 obs. of  6 variables:
#>   .. ..$ salutation : chr NA
#>   .. ..$ first_name : chr "Ken"
#>   .. ..$ middle_name: chr NA
#>   .. ..$ last_name  : chr "Binmore"
#>   .. ..$ suffix     : chr NA
#>   .. ..$ full_name  : chr "Ken Binmore"
#>   ..$ :'data.frame': 2 obs. of  6 variables:
#>   .. ..$ salutation : chr [1:2] NA NA
#>   .. ..$ first_name : chr [1:2] "Martin" "Ariel"
#>   .. ..$ middle_name: chr [1:2] "J." NA
#>   .. ..$ last_name  : chr [1:2] "Osborne" "Rubinstein"
#>   .. ..$ suffix     : chr [1:2] NA NA
#>   .. ..$ full_name  : chr [1:2] "Martin J. Osborne" "Ariel Rubinstein"
#>   ..$ :'data.frame': 2 obs. of  6 variables:
#>   .. ..$ salutation : chr [1:2] NA NA
#>   .. ..$ first_name : chr [1:2] "Adam" "Eddie"
#>   .. ..$ middle_name: chr [1:2] NA NA
#>   .. ..$ last_name  : chr [1:2] "Brandenburger" "Dekel"
#>   .. ..$ suffix     : chr [1:2] NA NA
#>   .. ..$ full_name  : chr [1:2] "Adam Brandenburger" "Eddie Dekel"
#>  $ BOOKTITLE   : chr [1:3] NA NA "The Economics of Missing Markets, Information and Games"
#>  $ CHAPTER     : chr [1:3] NA NA "3"
#>  $ CROSSREF    : chr [1:3] NA NA NA
#>  $ EDITION     : chr [1:3] NA NA NA
#>  $ EDITOR      :List of 3
#>   ..$ :'data.frame': 1 obs. of  6 variables:
#>   .. ..$ salutation : chr NA
#>   .. ..$ first_name : chr NA
#>   .. ..$ middle_name: chr NA
#>   .. ..$ last_name  : chr NA
#>   .. ..$ suffix     : chr NA
#>   .. ..$ full_name  : chr NA
#>   ..$ :'data.frame': 1 obs. of  6 variables:
#>   .. ..$ salutation : chr NA
#>   .. ..$ first_name : chr NA
#>   .. ..$ middle_name: chr NA
#>   .. ..$ last_name  : chr NA
#>   .. ..$ suffix     : chr NA
#>   .. ..$ full_name  : chr NA
#>   ..$ :'data.frame': 1 obs. of  6 variables:
#>   .. ..$ salutation : chr NA
#>   .. ..$ first_name : chr "Frank"
#>   .. ..$ middle_name: chr NA
#>   .. ..$ last_name  : chr "Hahn"
#>   .. ..$ suffix     : chr NA
#>   .. ..$ full_name  : chr "Frank Hahn"
#>  $ HOWPUBLISHED: chr [1:3] NA NA NA
#>  $ INSTITUTION : chr [1:3] NA NA NA
#>  $ JOURNAL     : chr [1:3] "Topoi" NA NA
#>  $ KEY         : chr [1:3] NA NA NA
#>  $ MONTH       : chr [1:3] NA NA NA
#>  $ NOTE        : chr [1:3] NA NA NA
#>  $ NUMBER      : chr [1:3] "1" NA NA
#>  $ ORGANIZATION: chr [1:3] NA NA NA
#>  $ PAGES       : chr [1:3] "17--27" NA "46--61"
#>  $ PUBLISHER   : chr [1:3] NA "The MIT Press, Cambridge, Massachusetts" "Oxford University Press"
#>  $ SCHOOL      : chr [1:3] NA NA NA
#>  $ SERIES      : chr [1:3] NA NA NA
#>  $ TITLE       : chr [1:3] "Do Conventions Need to Be Common Knowledge?" "A Course in Game Theory" "The Role of Common Knowledge Assumptions in Game Theory"
#>  $ TYPE        : chr [1:3] NA NA NA
#>  $ VOLUME      : chr [1:3] "27" NA NA
#>  $ YEAR        : num [1:3] 2008 1994 1989
```
