# A simple custom wrapper to create, configure and tune a workflowr project

This function automates the creation of a workflowr project. It
initializes the project, configures GitLab/GitHub, creates and
overwrites specific R Markdown files with predefined templates, replaces
placeholders, and publishes the initial site.

## Usage

``` r
wflow_datalabr(
  project_name,
  existing = FALSE,
  username,
  creator,
  domain = NULL,
  repo = c("GitHub", "GitLab"),
  attribution,
  lic = c("CCBY-NC-SA4.0", "gnu-gpl-v3")
)
```

## Arguments

- project_name:

  Character. The name of the project and repository.

- existing:

  Character. Checks if the package already exists.

- username:

  Character. Your username on the GitLab/GitHub instance.

- creator:

  Character. The name of the author or entity creating the project.

- domain:

  Character. The domain of the GitLab/GitHub instance (e.g.,
  "git.csic.es").

- repo:

  Character. The type of the repository to commit. Must be one of
  c("GitHub", "GitLab")

- attribution:

  Character. Attribution text for the license file.

- lic:

  Character. The license to apply. Must be one of "CCBY-NC-SA4.0"
  (default) or "gnu-gpl-v3".

## Value

Invisibly returns the project path upon successful creation.

## Examples

``` r
if (FALSE) { # \dontrun{
wflow_datalabr(
  project_name = "my_awesome_project",
  username = "Data Lab ICMAN",
  creator = "Data Lab ICMAN",
  domain = "git.csic.es",
  repo = "GitLab",
  attribution = "Data Lab ICMAN",
  lic = "CCBY-NC-SA4.0"
)
} # }
```
