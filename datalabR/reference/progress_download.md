# Create a progress bar for file downloads

Display a progress bar while downloading a file. Shows download speed
and estimated time remaining.

## Usage

``` r
progress_download(url, destfile, ..., style = "modern")
```

## Arguments

- url:

  URL to download from

- destfile:

  Destination file path

- ...:

  Additional arguments passed to
  [`download.file()`](https://rdrr.io/r/utils/download.file.html)

- style:

  Visual style of the progress bar

## Value

Invisible integer code (0 for success, non-zero for failure)

## Examples

``` r
if (FALSE) { # \dontrun{
# Download with progress
progress_download(
  "https://example.com/largefile.zip",
  "local_file.zip"
)

# Custom style
progress_download(
  "https://example.com/data.csv",
  "data.csv",
  style = "arrows"
)
} # }
```
