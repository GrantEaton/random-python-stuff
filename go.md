# Go

##### Channels and GoRoutines

* Create a goroutine with the `go` command:

`go func()`

**If the main func ends, all goroutines end**

* Example of creating go routines:
```
package main

import (  
    "fmt"
    "time"
)

func numbers() {  
    for i := 1; i <= 5; i++ {
        time.Sleep(250 * time.Millisecond)
        fmt.Printf("%d ", i)
    }
}
func alphabets() {  
    for i := 'a'; i <= 'e'; i++ {
        time.Sleep(400 * time.Millisecond)
        fmt.Printf("%c ", i)
    }
}
func main() {  
    go numbers()
    go alphabets()
    time.Sleep(3000 * time.Millisecond)
    fmt.Println("main terminated")
}
```

prints: `1 a 2 3 b 4 c 5 d e main terminated`

