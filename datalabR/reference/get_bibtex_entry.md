# Get a BibTeX entry from a DOI

Fetches a bibliographic entry in BibTeX format using a Digital Object
Identifier (DOI).

## Usage

``` r
get_bibtex_entry(doi)
```

## Arguments

- doi:

  A character string representing the DOI of the article.

## Value

A character string with the entry in BibTeX format. Returns `NULL` if
the DOI is invalid, not found, or the request fails.

## Examples

``` r
if (FALSE) { # \dontrun{
entry <- get_bibtex_entry("10.1126/science.1172133")
if (!is.null(entry)) {
  cat(entry)
}
} # }
```
