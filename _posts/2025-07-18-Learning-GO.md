---
layout : post
date : 2025-07-18
title  : Learning Go-lang
---

## Learning GO to get the minimum latency and get things right from start .. 


The whole file needs to become a package and to make it whole a package we wrap that up in `package main` and this makes the whole code as a single package that is then converted to binary 

### Imports 
The internal imports are done using: 

```
import (
  "fmt"
  "net/http"
  "github.com/gorilla/mux"
)
```

so these are the imports as we made in the python and to get these imported sorted we have to take 2 steps

```

1. `go mod init <package-name>` : can be named anything, we need this to make sure the module is go.mod and public and anyone can download and use the functions / classes listed in it ..

2. `go mod tidy` : this is like pip install -r r.txt where in python we write the library names in r.txt here we write the libraries in code itself and we they gets installed and added as require in the mod file
```

`func main()` is the function that gets called by default as soon as we compile the app 

`go run .` : runs the file 




