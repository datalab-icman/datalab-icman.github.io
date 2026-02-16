# Apply a function with a colorful progress bar

Apply a function over a vector or list with a beautiful progress bar
showing progress. Similar to
[`lapply()`](https://rdrr.io/r/base/lapply.html) but with rich visual
feedback including colors and Unicode symbols.

## Usage

``` r
progress_apply(
  X,
  FUN,
  ...,
  .format = "{bar} {percent} {eta}",
  .style = "modern",
  .width = NULL,
  .clear = TRUE,
  .show_after = 0.2
)
```

## Arguments

- X:

  A vector or list to iterate over

- FUN:

  Function to apply to each element

- ...:

  Additional arguments passed to FUN

- .format:

  Format string for the progress bar

- .style:

  Visual style of the progress bar

- .width:

  Width of the progress bar

- .clear:

  Whether to clear the bar on completion

- .show_after:

  Seconds to wait before showing the bar

## Value

A list of results from applying FUN to each element of X

## Examples

``` r
if (FALSE) { # \dontrun{
# Simple example
results <- progress_apply(1:20, function(x) {
  Sys.sleep(0.1)
  x^2
})

# Reading files with progress
files <- list.files(pattern = "\\.csv$")
data_list <- progress_apply(
  files,
  read.csv,
  .format = "{spin} {bar} {current}/{total} files",
  .style = "elegant"
)

# Data processing with custom style
results <- progress_apply(
  1:100,
  function(x) {
    Sys.sleep(0.02)
    rnorm(100, mean = x)
  },
  .format = "{bar} {percent} | {rate}",
  .style = "blocks"
)

# Keep progress bar after completion
results <- progress_apply(
  datasets,
  process_data,
  .format = "{spin} Processing {bar} {current}/{total}",
  .clear = FALSE
)
} # }
```
