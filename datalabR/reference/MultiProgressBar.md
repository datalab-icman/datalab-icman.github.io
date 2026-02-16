# Create a multi-bar progress display

Manage multiple progress bars simultaneously, useful for tracking
parallel operations or multiple stages of a process. Each bar can have
its own style and format.

## Public fields

- `bars`:

  List of progress bars

## Methods

### Public methods

- [`MultiProgressBar$new()`](#method-MultiProgressBar-new)

- [`MultiProgressBar$add_bar()`](#method-MultiProgressBar-add_bar)

- [`MultiProgressBar$remove_bar()`](#method-MultiProgressBar-remove_bar)

- [`MultiProgressBar$terminate_all()`](#method-MultiProgressBar-terminate_all)

- [`MultiProgressBar$clone()`](#method-MultiProgressBar-clone)

------------------------------------------------------------------------

### Method `new()`

Create a new multi-bar progress display

#### Usage

    MultiProgressBar$new(stream = stderr())

#### Arguments

- `stream`:

  Output stream (default: stderr())

#### Returns

A new `MultiProgressBar` object

------------------------------------------------------------------------

### Method `add_bar()`

Add a new progress bar to the display

#### Usage

    MultiProgressBar$add_bar(
      id,
      total,
      format = "{bar} {percent}",
      style = "modern",
      ...
    )

#### Arguments

- `id`:

  Unique identifier for this bar

- `total`:

  Total number of iterations

- `format`:

  Format string

- `style`:

  Visual style

- `...`:

  Additional arguments passed to ProgressBar\$new()

#### Returns

The created ProgressBar object

------------------------------------------------------------------------

### Method `remove_bar()`

Remove a progress bar

#### Usage

    MultiProgressBar$remove_bar(id)

#### Arguments

- `id`:

  Identifier of the bar to remove

#### Returns

Invisible self

------------------------------------------------------------------------

### Method `terminate_all()`

Terminate all progress bars

#### Usage

    MultiProgressBar$terminate_all()

#### Returns

Invisible self

------------------------------------------------------------------------

### Method `clone()`

The objects of this class are cloneable with this method.

#### Usage

    MultiProgressBar$clone(deep = FALSE)

#### Arguments

- `deep`:

  Whether to make a deep clone.

## Examples

``` r
if (FALSE) { # \dontrun{
# Track multiple operations
mb <- MultiProgressBar$new()

# Add bars for different tasks
pb1 <- mb$add_bar(
  id = "download",
  total = 100,
  format = "{spin} Download {bar} {percent}",
  style = "modern"
)

pb2 <- mb$add_bar(
  id = "process",
  total = 50,
  format = "{spin} Process  {bar} {percent}",
  style = "elegant"
)

pb3 <- mb$add_bar(
  id = "upload",
  total = 80,
  format = "{spin} Upload   {bar} {percent}",
  style = "blocks"
)

# Simulate work
for (i in 1:100) {
  if (i <= 100) pb1$tick()
  if (i <= 50) pb2$tick()
  if (i <= 80) pb3$tick()
  Sys.sleep(0.02)
}

mb$terminate_all()
} # }
```
