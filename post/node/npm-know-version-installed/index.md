---
title: Find the installed version of an npm package
description: "How to find out which version of a particular package you have installed in your app"
date: 2018-08-08T07:00:00+02:00
tags: node
tags_weight: 23
path: npm-know-version-installed
---

To see the latest version of all the npm package installed, including their dependencies:

```bash
npm list
```

Example:

```txt
❯ npm list
/Users/flavio/dev/node/cowsay
└─┬ cowsay@1.3.1
  ├── get-stdin@5.0.1
  ├─┬ optimist@0.6.1
  │ ├── minimist@0.0.10
  │ └── wordwrap@0.0.3
  ├─┬ string-width@2.1.1
  │ ├── is-fullwidth-code-point@2.0.0
  │ └─┬ strip-ansi@4.0.0
  │   └── ansi-regex@3.0.0
  └── strip-eof@1.0.0
```

You can also just open the `package-lock.json` file, but this involves some visual scanning.

`npm list -g` is the same, but for globally installed packages.

To get only your top-level packages (basically, the ones you told npm to install and you listed in the `package.json`), run `npm list --depth=0`:

```txt
❯ npm list --depth=0
/Users/flavio/dev/node/cowsay
└── cowsay@1.3.1
```

You can get the version of a specific package by specifying the name:

```txt
❯ npm list cowsay
/Users/flavio/dev/node/cowsay
└── cowsay@1.3.1
```

This also works for dependencies of packages you installed:

```txt
❯ npm list minimist
/Users/flavio/dev/node/cowsay
└─┬ cowsay@1.3.1
  └─┬ optimist@0.6.1
    └── minimist@0.0.10
```

If you want to see what's the latest available version of the package on the npm repository, run `npm view [package_name] version`:

```txt
❯ npm view cowsay version

1.3.1
```
