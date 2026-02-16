# datalabR [![datalabR hex logo](reference/figures/datalabr_hex.png)](https://datalab-icman.github.io/datalabR)

  

Provides a suite of useful tools from the Data Lab ICMAN.

## Installation

You can install the development version:

``` r
if (!require("pak")) install.packages("pak")
pak::pak("datalab-icman/datalabR")
```

## Example

``` r
library(datalabR)
```

Show some Unicode symbols:

``` r
show_symbol_legend()
#> 
#> --- Package Console Symbol Legend ---
#> 
#> STATUS MESSAGES:
#>  ✅ Success/Approved: Task completed successfully.
#>  ❌ Error/Failure: Task could not be completed due to an issue.
#>  ⚠️ Warning: Task completed, but with potential issues or anomalies.
#>  ⛔️ Forbidden/Stopped: Action is not valid or has been restricted.
#> 
#> PROGRESS & ACTIONS:
#>  ⚙️ Configuration/Setup: Starting a configuration or pre-processing step.
#>  🚀 Rocket Launch/Quick Start: Initiating a critical process or deployment.
#>  ⏳ In Progress/Waiting: Task is currently running and may take time.
#>  ⌛️ Time Completed: The waiting period or process has finished.
#>  🔍 Search/Investigation: Executing a query or data exploration function.
#>  📁 Directory/File: Creating or accessing a file path/folder.
#>  💾 Save/Write: Data has been successfully written to disk.
#> 
#> INFORMATIONAL:
#>  ℹ️ Information: General informational or debugging message.
#>  💡 Hint/Idea: A useful tip or additional note for the user.
#>  🎉 Celebration: Milestone reached or installation complete!
#> 
#> --------------------------------------
```
