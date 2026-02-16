# Create a progress bar for loops and iterations

A convenience function to create a colorful progress bar with Unicode
symbols. This is a simple wrapper around `ProgressBar$new()` with
sensible defaults.

## Usage

``` r
progress_bar(
  total = 100,
  format = "{bar} {percent} {eta}",
  style = "modern",
  ...
)
```

## Arguments

- total:

  Total number of iterations

- format:

  Format string with tokens (default: "bar percent eta")

- style:

  Visual style (default: "modern")

- ...:

  Additional arguments passed to `ProgressBar$new()`

## Value

A `ProgressBar` object

## Examples

``` r
if (FALSE) { # \dontrun{
# Simple loop with progress bar
pb <- progress_bar(total = 100)
for (i in 1:100) {
  pb$tick()
  Sys.sleep(0.02)
}

# Custom style and format
pb <- progress_bar(
  total = 50,
  format = "{spin} Working {bar} {percent}",
  style = "elegant"
)
for (i in 1:50) {
  pb$tick()
  Sys.sleep(0.05)
}

# With status messages
pb <- progress_bar(
  total = 30,
  format = "{bar} {current}/{total} | {msg}",
  style = "circles"
)
for (i in 1:30) {
  pb$tick(tokens = list(msg = paste("Processing item", i)))
  Sys.sleep(0.1)
}
} # }
```
