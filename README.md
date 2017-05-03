# One-time redirect for Gerrit out-of-the-box experience

Plugin to provide an out-of-the-box redirect for a fresh Gerrit install

## Background

When preparing a native packaging of Gerrit Code Review, the initial
"out of the box" experience is necessary.

At the very first access to Gerrit UX, the browser gets redirected to
a pre-configured URL which typically points to an introduction page.

## How to build

Create a symbolic link to the out-of-the-box repository from the Gerrit
source code /plugins directory to the subdirectories of this project.

Then build the out-of-the-box plugin with the usual Gerrit plugin compile command.

Example:

```
$ git clone https://github.com/GerritForge/out-of-the-box
$ git clone https://gerrit.googlesource.com/gerrit
$ cd gerrit/plugins
$ ln -s ../../out-of-the-box .
$ cd ..
$ bazel build plugins/out-of-the-box
```

## How to install and configure

This plugin needs to be located in the Gerrit /lib directory and can be configured
from the gerrit.config httpd directory as additional servlet filter in the
httpd.filterClass setting.

The URL for the initial redirection URL is then configured in the
http.firstTimeRedirectUrl setting.

Example gerrit.config:

```
[httpd]
  filterClass = com.googlesource.gerrit.plugins.manager.FirstTimeRedirect
  firstTimeRedirectUrl = https://mycompany.com/gerrit-intro.html
```

__NOTE:__ The redirection happens only *ONCE* at the very first access to Gerrit UX.
After that a flag file gets create under $GERRIT_SITE directory (.firstTimeRedirect)
and the redirection filter will not be effective anymore.
