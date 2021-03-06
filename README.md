
[![Travis build
status](https://travis-ci.com/muschellij2/recordscreen.svg?branch=master)](https://travis-ci.com/muschellij2/recordscreen)
[![AppVeyor Build
Status](https://ci.appveyor.com/api/projects/status/github/muschellij2/recordscreen?branch=master&svg=true)](https://ci.appveyor.com/project/muschellij2/recordscreen)
[![Coverage
status](https://codecov.io/gh/muschellij2/recordscreen/branch/master/graph/badge.svg)](https://codecov.io/gh/muschellij2/recordscreen)
<!-- README.md is generated from README.Rmd. Please edit that file -->

# recordscreen Package:

The goal of `recordscreen` is to provide functions to reccord the screen
with `ffmpeg` to be able to show script execution. A system installation
`ffmpeg` is required, run to see if `ffmpeg` is in your `PATH`:

``` r
Sys.which("ffmpeg")
```

## Errors with Mac OSX Mojave and RStudio

You need to authorize RStudio to use the mic/camera in Mojave. The
changes were due to this:
<https://developer.apple.com/documentation/avfoundation/cameras_and_media_capture/requesting_authorization_for_media_capture_on_macos>
and fixed here <https://github.com/rstudio/rstudio/issues/4579>

If you an’t access video/audio from RStudio IDE, then see issue here
<https://github.com/rstudio/rstudio/issues/4579>. If you run into this,
make sure you have RStudio version \>= 1.3. To access this version
download daily build <https://dailies.rstudio.com/>, authorize (use
audio and opencv packages for force auth)

``` r
if (!requireNamespace("opencv"))
  install.packages("opencv")

library(opencv)
ocv_video(ocv_edges)
```

``` r
if (!requireNamespace("audio"))
  install.packages("audio")

library(audio)
x <- rep(NA_real_, 50000)
# start recording into x
record(x, 22000, 1)
stopifnot(diff(range(x, na.rm = TRUE)) > 0)
```

Then download whatever RStudio you want.

  - Make sure you go to System Preferences \#\# Installation

You can install `recordscreen` from GitHub with:

``` r
# install.packages("remotes")
remotes::install_github("muschellij2/recordscreen")
```
