# Show a progress bar for a specific duration

Display a progress bar that fills up over a specified time duration.
Useful for showing progress during time-based operations or simulations.

## Usage

``` r
progress_sleep(
  seconds,
  format = "{bar} {elapsed}/{eta}",
  style = "modern",
  steps = 100,
  ...
)
```

## Arguments

- seconds:

  Duration in seconds

- format:

  Format string for the progress bar

- style:

  Visual style of the progress bar

- steps:

  Number of update steps (default: 100)

- ...:

  Additional arguments passed to `ProgressBar$new()`

## Value

Invisible NULL

## Examples

``` r
if (FALSE) { # \dontrun{
# Wait 5 seconds with progress
progress_sleep(5)

# Custom format
progress_sleep(
  10,
  format = "{spin} Waiting {bar} {elapsed}/{eta}",
  style = "elegant"
)

# More granular updates
progress_sleep(
  3,
  format = "{bar} {percent}",
  style = "dots",
  steps = 50
)
} # }
```
