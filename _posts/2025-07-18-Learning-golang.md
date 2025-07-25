---
layout : post
date : 2025-07-18
title  : Learning Go-lang
---

## Learning GO to get the minimum latency and get things right from start .. 
[Go docs](https://go.dev/doc/tutorial/getting-started)  
[Go Tour](https://go.dev/tour/list)

The whole file needs to become a package and to make it whole a package we wrap that up in `package main` and this makes the whole code as a single package that is then converted to binary 

We create package to help us import those in other files and the importing helps in code seperation, else we would have to write the whole code in a single main.go file.. 


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


### Multiple modules 

If each module in a separate directory, you will need to basically convert that package from external link to the local one :

```
~/go-dev/
├── greetings/
│   └── go.mod (module example.com/greetings)
|   └── greetings.go 
└── app/
    └── go.mod (module example.com/app)
    └── app.go 
```

So to use greetings.go in app.go we need to import in this way in the 
`go mod edit --replace example.com/greeting=../greetings`

also the package name should be same as the directory name .. 

### Variable declaration 

```
var name string
name = "Mohit"
--
name := "Hello" //Here the type declaration is taken from the rght side of the string 
```

`list` declaration:

```
message := [] string { 
  "Hi 1", 
  "Hi 2",
  "Hi 3",
}
```

### Error Handling 

send the value , error with it  .. 

so the return is a tuple ( message , error-code ) , error return nil means no error , else send an erorr using : 

```
import "errors"

if name == "":
  return "", errors.New("empty name")
```






