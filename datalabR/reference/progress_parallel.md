# Progress bar for parallel operations

A wrapper around
[`parallel::mclapply()`](https://rdrr.io/r/parallel/mclapply.html) or
[`parallel::parLapply()`](https://rdrr.io/r/parallel/clusterApply.html)
that shows a progress bar. This function provides visual feedback for
parallel processing operations.

## Usage

``` r
progress_parallel(
  X,
  FUN,
  ...,
  .mc.cores = getOption("mc.cores", 2L),
  .format = "{bar} {percent} {eta}",
  .style = "modern",
  .method = c("fork", "psock")
)
```

## Arguments

- X:

  A vector or list to iterate over

- FUN:

  Function to apply to each element

- ...:

  Additional arguments passed to FUN

- .mc.cores:

  Number of cores to use (Unix-like systems only)

- .format:

  Format string for the progress bar

- .style:

  Visual style of the progress bar

- .method:

  Method to use: "fork" (Unix) or "psock" (Windows/Unix)

## Value

A list of results from applying FUN to each element of X

## Examples

``` r
if (FALSE) { # \dontrun{
# Parallel processing with progress (Unix-like systems)
results <- progress_parallel(
  1:100,
  function(x) {
    Sys.sleep(0.1)
    x^2
  },
  .mc.cores = 4,
  .format = "{spin} {bar} {percent} | {current}/{total}",
  .style = "modern"
)

# Works on all platforms with PSOCK method
results <- progress_parallel(
  large_dataset,
  expensive_function,
  .method = "psock",
  .mc.cores = 4,
  .style = "elegant"
)
} # }
```
