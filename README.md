# RStudio Project Example
This repository contains a basic, demonstrative example for an [RStudio Community forum post] relating to calling `rsconnect::writeManifest` from projects using [`packrat`]. 

## Problem Description

When calling `rsconnect::writeManifest`, at least on macOS 10.14.5, the function fails with the following error in projects that use `packrat`:

```
Error in data.frame(Source = source, Repository = repository) : 
  arguments imply differing number of rows: 1, 0
```

With some effort, I managed to locate the source of the error in [`rsconnect:::snapshotDependencies`]. The error is being thrown by the following line:

```
data.frame(Source = source, Repository = repository)
```

A detailed discussion of the issue can be found on the [RStudio Community forum post].

This repository contains an example project that _does not_ use `packrat`.

## Running the Example

1. Open `basic-shiny-app-packrat.Rproj` in RStudio.

2. If not already installed, install the `rsconnect` package (i.e. `install.packages("rsconnect")`).

3. Call `rsconnect::writeManifest()`; the call should succeed without any errors.


[RStudio Community forum post]: https://community.rstudio.com/t/rsconnect-writemanifest-fails-in-projects-using-packrat/36634
[`packrat`]: https://rstudio.github.io/packrat
[`rsconnect:::snapshotDependencies`]: https://rdrr.io/cran/rsconnect/src/R/dependencies.R#sym-snapshotDependencies
