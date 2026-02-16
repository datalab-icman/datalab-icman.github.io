# Iterate over elements with a visual progress bar

A wrapper that provides a colorful progress bar with Unicode symbols for
any iterable object. Returns an enhanced vector/list that displays
progress when used in a for loop with the special `progress_iterate()`
wrapper.

## Usage

``` r
progress_iterate(x, format = "{bar} {percent} {eta}", style = "modern", ...)
```

## Arguments

- x:

  A vector or list to iterate over

- format:

  Format string for the progress bar

- style:

  Visual style of the progress bar

- ...:

  Additional arguments passed to `ProgressBar$new()`

## Value

The input object with progress tracking enabled

## Examples

``` r
if (FALSE) { # \dontrun{
# Basic iteration
for (i in progress_iterate(1:100)) {
  # Your code here
  Sys.sleep(0.02)
}

# With custom format
for (item in progress_iterate(
  my_list,
  format = "{spin} {bar} {current}/{total}",
  style = "elegant"
)) {
  process(item)
  Sys.sleep(0.1)
}

# Different styles
for (file in progress_iterate(
  files,
  format = "{bar} {percent} | Processing files",
  style = "circles"
)) {
  data <- read.csv(file)
  Sys.sleep(0.05)
}

# Arrows style for downloads
urls <- c("url1", "url2", "url3")
for (url in progress_iterate(urls, style = "arrows")) {
  download_file(url)
}
} # }
```
