# Progress bar class with colored Unicode symbols

A comprehensive and visually appealing progress bar implementation with
colored Unicode symbols, spinners, and rich formatting options. Inspired
by the cli package but standalone and fully self-contained.

## Details

This progress bar system provides:

- Beautiful Unicode box-drawing characters and symbols

- ANSI color support with automatic terminal detection

- Multiple built-in styles (modern, classic, elegant, minimal, dots,
  arrows)

- Customizable colors for complete, current, and incomplete sections

- Animated spinners with various styles

- Automatic ETA and rate calculations

- Terminal width detection and responsive layout

- Clean completion and interruption handling

## Format tokens

The following tokens can be used in the format string:

- `{bar}` - The progress bar itself with colored symbols

- `{current}` - Current iteration number

- `{total}` - Total number of iterations

- `{percent}` - Percentage complete (e.g., "45%")

- `{elapsed}` - Time elapsed since start

- `{eta}` - Estimated time to completion

- `{rate}` - Iterations per second

- `{spin}` - Animated spinning indicator

- `{status}` - Custom status message

- Any custom token passed via the `tokens` parameter

## Color support

Colors are automatically enabled if the terminal supports ANSI colors.
You can force enable/disable colors with the `use_colors` parameter.
Available colors: black, red, green, yellow, blue, magenta, cyan, white,
and their bright variants (e.g., "bright_green").

## Built-in styles

- `modern` - Colorful boxes with smooth gradients (default)

- `classic` - Traditional equal signs and dashes

- `elegant` - Unicode block elements with subtle colors

- `minimal` - Simple dots, clean and fast

- `dots` - Circular dots that fill up

- `arrows` - Arrow symbols pointing right

- `blocks` - Solid and shaded Unicode blocks

- `circles` - Circular progress indicators

## Public fields

- `total`:

  Total number of ticks

- `current`:

  Current tick count

- `width`:

  Width of the progress bar

- `format`:

  Format string for display

- `clear`:

  Whether to clear the progress bar on completion

- `show_after`:

  Show progress bar after this many seconds

- `style`:

  Visual style of the progress bar

## Methods

### Public methods

- [`ProgressBar$new()`](#method-ProgressBar-new)

- [`ProgressBar$tick()`](#method-ProgressBar-tick)

- [`ProgressBar$update()`](#method-ProgressBar-update)

- [`ProgressBar$terminate()`](#method-ProgressBar-terminate)

- [`ProgressBar$ratio()`](#method-ProgressBar-ratio)

- [`ProgressBar$elapsed()`](#method-ProgressBar-elapsed)

- [`ProgressBar$set_style()`](#method-ProgressBar-set_style)

- [`ProgressBar$clone()`](#method-ProgressBar-clone)

------------------------------------------------------------------------

### Method `new()`

Create a new progress bar with colored Unicode symbols

#### Usage

    ProgressBar$new(
      total = 100,
      format = "{bar} {percent} {eta}",
      width = NULL,
      style = "modern",
      complete_color = "green",
      current_color = "yellow",
      incomplete_color = "white",
      current = 0,
      clear = TRUE,
      show_after = 0.2,
      use_colors = NULL,
      force = FALSE,
      stream = stderr()
    )

#### Arguments

- `total`:

  Total number of iterations

- `format`:

  Format string with tokens (default: "bar percent eta")

- `width`:

  Width of the progress bar in characters (default: auto-detect)

- `style`:

  Visual style: "modern", "classic", "elegant", "minimal", "dots",
  "arrows", "blocks", or "circles" (default: "modern")

- `complete_color`:

  Color for completed portion (default: "green")

- `current_color`:

  Color for the current position indicator (default: "yellow")

- `incomplete_color`:

  Color for incomplete portion (default: "white")

- `current`:

  Starting position (default: 0)

- `clear`:

  Clear bar on completion (default: TRUE)

- `show_after`:

  Delay in seconds before showing (default: 0.2)

- `use_colors`:

  Force enable/disable colors (default: auto-detect)

- `force`:

  Force display in non-interactive sessions (default: FALSE)

- `stream`:

  Output stream (default: stderr())

#### Returns

A new `ProgressBar` object

------------------------------------------------------------------------

### Method `tick()`

Increment the progress bar by one or more steps

#### Usage

    ProgressBar$tick(len = 1, tokens = list())

#### Arguments

- `len`:

  Number of steps to advance (default: 1)

- `tokens`:

  Named list of custom tokens to display

#### Returns

Invisible self for method chaining

------------------------------------------------------------------------

### Method [`update()`](https://rdrr.io/r/stats/update.html)

Update the progress bar to a specific position

#### Usage

    ProgressBar$update(current, tokens = list())

#### Arguments

- `current`:

  New current position (0 to total)

- `tokens`:

  Named list of custom tokens to display

#### Returns

Invisible self for method chaining

------------------------------------------------------------------------

### Method `terminate()`

Mark the progress bar as complete and clean up

#### Usage

    ProgressBar$terminate(tokens = list())

#### Arguments

- `tokens`:

  Named list of custom tokens for final display

#### Returns

Invisible self

------------------------------------------------------------------------

### Method `ratio()`

Get the current progress as a ratio between 0 and 1

#### Usage

    ProgressBar$ratio()

#### Returns

Numeric value between 0 and 1

------------------------------------------------------------------------

### Method `elapsed()`

Get elapsed time since progress bar creation

#### Usage

    ProgressBar$elapsed()

#### Returns

Numeric elapsed time in seconds

------------------------------------------------------------------------

### Method `set_style()`

Change the style of the progress bar on the fly

#### Usage

    ProgressBar$set_style(style)

#### Arguments

- `style`:

  New style name

#### Returns

Invisible self

------------------------------------------------------------------------

### Method `clone()`

The objects of this class are cloneable with this method.

#### Usage

    ProgressBar$clone(deep = FALSE)

#### Arguments

- `deep`:

  Whether to make a deep clone.

## Examples

``` r
if (FALSE) { # \dontrun{
# Basic usage with default modern style
pb <- ProgressBar$new(total = 100)
for (i in 1:100) {
  pb$tick()
  Sys.sleep(0.02)
}

# Different styles showcase
styles <- c("modern", "elegant", "dots", "arrows", "blocks", "circles")
for (style in styles) {
  cat("\nStyle:", style, "\n")
  pb <- ProgressBar$new(
    total = 50,
    format = "{spin} {bar} {percent} | {style}",
    style = style,
    width = 40
  )
  for (i in 1:50) {
    pb$tick(tokens = list(style = style))
    Sys.sleep(0.01)
  }
}

# Custom colors and format
pb <- ProgressBar$new(
  total = 100,
  format = "{spin} Processing {bar} {percent} | ETA: {eta}",
  complete_color = "bright_green",
  current_color = "bright_yellow",
  incomplete_color = "bright_black",
  width = 60
)
for (i in 1:100) {
  pb$tick()
  Sys.sleep(0.02)
}

# File processing with custom tokens
files <- paste0("data_file_", 1:25, ".csv")
pb <- ProgressBar$new(
  total = length(files),
  format = "{spin} {bar} {current}/{total} | Processing: {filename}",
  style = "elegant",
  show_after = 0
)
for (f in files) {
  # Simulate file processing
  pb$tick(tokens = list(filename = f))
  Sys.sleep(0.1)
}

# Data processing with status updates
pb <- ProgressBar$new(
  total = 200,
  format = "{spin} {bar} {percent} | {status}",
  style = "blocks"
)
for (i in 1:200) {
  status <- if (i %% 50 == 0) "Checkpoint saved" else "Processing..."
  pb$tick(tokens = list(status = status))
  Sys.sleep(0.01)
}

# Minimal style for fast operations
pb <- ProgressBar$new(
  total = 1000,
  format = "{bar} {current}/{total} {rate}",
  style = "minimal",
  clear = FALSE
)
for (i in 1:1000) {
  pb$tick()
  Sys.sleep(0.001)
}

# Long-running task with detailed info
pb <- ProgressBar$new(
  total = 500,
  format = paste0(
    "{spin} Analysis {bar} {percent}\n",
    "├─ Completed: {current}/{total} items\n",
    "├─ Speed: {rate}\n",
    "└─ ETA: {eta}"
  ),
  style = "modern",
  width = 50
)
for (i in 1:500) {
  pb$tick()
  Sys.sleep(0.005)
}

# Using update() instead of tick()
pb <- ProgressBar$new(total = 100, style = "circles")
for (i in seq(0, 100, by = 5)) {
  pb$update(i, tokens = list(status = paste("Step", i)))
  Sys.sleep(0.1)
}

# Downloading simulation
pb <- ProgressBar$new(
  total = 100,
  format = "{spin} Downloading {bar} {percent} | {speed} MB/s | {eta}",
  style = "arrows"
)
for (i in 1:100) {
  speed <- round(runif(1, 1.5, 5.5), 1)
  pb$tick(tokens = list(speed = speed))
  Sys.sleep(0.03)
}
} # }
```
