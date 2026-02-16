# Build, document, check, and install R package

A comprehensive function to manage all aspects of R package development,
including formatting, documentation, building, checking, installing, and
website deployment.

## Usage

``` r
build_pkg(
  pkg_path = ".",
  session_info = TRUE,
  style_code = TRUE,
  compile_rcpp = TRUE,
  use_roxygen_md = TRUE,
  document = TRUE,
  use_pkg_doc = TRUE,
  load_all = TRUE,
  build = FALSE,
  check = FALSE,
  check_error_on = "never",
  install = TRUE,
  install_upgrade = "never",
  install_build = FALSE,
  build_site = FALSE,
  deploy_site = FALSE,
  site_source = "docs",
  site_destination = NULL,
  verbose = TRUE,
  use_devtools = TRUE
)
```

## Arguments

- pkg_path:

  Character. Path to the package directory. Default is "." (current
  directory).

- session_info:

  Logical. Print R session information? Default is TRUE.

- style_code:

  Logical. Format code using styler? Default is TRUE.

- compile_rcpp:

  Logical. Compile Rcpp attributes? Default is TRUE.

- use_roxygen_md:

  Logical. Configure roxygen2 to use Markdown? Default is TRUE.

- document:

  Logical. Generate documentation and NAMESPACE? Default is TRUE.

- use_pkg_doc:

  Logical. Set up package-level documentation? Default is TRUE.

- load_all:

  Logical. Load the package into the R session? Default is TRUE.

- build:

  Logical. Build the package tarball? Default is FALSE.

- check:

  Logical. Run R CMD check? Default is FALSE.

- check_error_on:

  Character. Level of issues to treat as errors in check. Options:
  "never", "warning", "error", "note". Default is "never".

- install:

  Logical. Install the package locally? Default is TRUE.

- install_upgrade:

  Character. Upgrade dependencies during install? Options: "default",
  "ask", "always", "never". Default is "never".

- install_build:

  Logical. Build vignettes during installation? Default is FALSE.

- build_site:

  Logical. Build pkgdown website? Default is FALSE.

- deploy_site:

  Logical. Copy pkgdown site to deployment folder? Default is FALSE.

- site_source:

  Character. Source folder for pkgdown site. Default is "docs".

- site_destination:

  Character. Destination folder for deployment. Default is NULL (must be
  specified if deploy_site = TRUE).

- verbose:

  Logical. Print detailed progress messages? Default is TRUE.

- use_devtools:

  Logical. Use devtools functions (TRUE) or base R/system commands
  (FALSE)? Default is TRUE.

## Value

Invisible NULL. The function is called for its side effects.

## Details

This function provides a unified interface for all common R package
development tasks. It combines the functionality of multiple tools:

- styler for code formatting

- Rcpp for C++ integration

- roxygen2/devtools for documentation

- R CMD build/check for quality control

- pkgdown for website generation

The function can use either devtools-based workflow (recommended for
interactive use) or system command-based workflow (useful for automated
builds and CI/CD).

Required packages are checked automatically and helpful installation
messages are provided if any are missing.

## Examples

``` r
if (FALSE) { # \dontrun{
# Quick development cycle (document and load)
build_pkg(check = FALSE, install = FALSE)

# Full build and check
build_pkg(build = TRUE, check = TRUE, install = TRUE)

# Prepare for CRAN submission
build_pkg(
  style_code = TRUE, build = TRUE, check = TRUE,
  check_error_on = "warning", install = FALSE
)

# Build and deploy website
build_pkg(
  build_site = TRUE, deploy_site = TRUE,
  site_destination = "../my-website/_site/mypkg"
)

# Automated build using system commands
build_pkg(use_devtools = FALSE, build = TRUE, check = TRUE, install = TRUE)
} # }
```
