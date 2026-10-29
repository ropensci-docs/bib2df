# Changelog

## bib2df 1.1.0

- This version fixes failing unit tests on CRAN.
- This version will be published on CRAN.

## bib2df 1.0.1

CRAN release: 2018-06-02

- This package versions fixes some issues:
  - [`bib2df()`](https://docs.ropensci.org/bib2df/reference/bib2df.md)
    can now read `.bib` files with a single entry
  - [`bib2df()`](https://docs.ropensci.org/bib2df/reference/bib2df.md)
    now allows `@` symbol within titles
- This version will be published on CRAN since version 1.0.0 had beed
  removed from CRAN due to check errors.

## bib2df 1.0.0

CRAN release: 2017-09-18

- This package version went successfully through the `rOpenSci`
  onboarding process.
- The package now support AppVeyor builds.
- This version contains aditional unit tests.

## bib2df 0.2.2

- Changes due to the ropensci review process:
  - Improved behavior on malformed .bib files and entries
  - Improved behavior on type conversion
  - [`df2bib()`](https://docs.ropensci.org/bib2df/reference/df2bib.md)
    is now able to append to an existing file
  - Minor changes in documentation and vignette

## bib2df 0.2.1

- Changes due to the ropensci review process:
  - Improved formatting
  - Removed exports of internal functions
  - Improved vignette

## bib2df 0.2

CRAN release: 2017-05-21

- Standardized return value for
  [`bib2df()`](https://docs.ropensci.org/bib2df/reference/bib2df.md)
  ([\#5](https://github.com/ropensci/bib2df/issues/5),
  [@leeper](https://github.com/leeper))
- Added functionality to write `data.frame` back to BibTeX file
  ([`df2bib()`](https://docs.ropensci.org/bib2df/reference/df2bib.md))
  ([\#5](https://github.com/ropensci/bib2df/issues/5),
  [@leeper](https://github.com/leeper))
- Adds a testthat-based tests for both
  [`bib2df()`](https://docs.ropensci.org/bib2df/reference/bib2df.md) and
  [`df2bib()`](https://docs.ropensci.org/bib2df/reference/df2bib.md)
  ([\#5](https://github.com/ropensci/bib2df/issues/5),
  [@leeper](https://github.com/leeper))
- Added functionality of the `humaniformat` package to split up names
  ([\#4](https://github.com/ropensci/bib2df/issues/4))
