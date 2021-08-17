---
title: "GoLogger - Module to Log with formatting in Golang"
date: "2017-07-11"
categories: 
  - "golang"
tags: 
  - "logging"
  - "logrus"
---

[GoLogger](https://github.com/alknopfler/Gologger) is a logger module for golang based on logrus module. This module was created to reduce the logrus abstraction in order to use just 2 functions:

- Init() : initialize the logrus params
- Print(): Print an error with the base fields

**Usage:**

\*\* Import package \*\*

```
import (

    "github.com/alknopfler/Gologger/gologger"
    )
```

**Init with stdout and info level:**

```
gologger.Init(os.Stdout, logrus.InfoLevel)
```

**Print to show the error message:**

```
gologger.Print("WARN",7,"Description to show","filename.go")
```
