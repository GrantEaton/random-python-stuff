# Go
### Concurrency 
#### GoRoutines

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

#### Channels 
```
Channels can be thought as pipes using which Goroutines communicate. Similar to how water flows from one end to another in a pipe, data can be sent from one end and received from the another end using channels.
Channels will lock the thread where the channel is created until there is data written to that channel.
```

* Create and allocate a channel 

`var c chan int`
`c = make(chan int)`

or in one line...

`done := make(chan bool)`

* Read and write to a channel
```
data := <- a // read from channel a  
a <- data // write to channel a
```

* Example of using a channel:
```
package main

import (  
    "fmt"
)

func hello(done chan bool) {  
    fmt.Println("Hello world goroutine")
    done <- true
}
func main() {  
    done := make(chan bool)
    go hello(done)
    <-done
    fmt.Println("main function")
}
```
prints 
```
Hello world goroutine  
main function  
```

* Check if channel is open

`v, ok := <- ch`

`ok` is true if open.

* Generic loop over channel and get data from it
```
package main

import (  
    "fmt"
)

func producer(chnl chan int) {  
    for i := 0; i < 10; i++ {
        chnl <- i
    }
    close(chnl)
}
func main() {  
    ch := make(chan int)
    go producer(ch)
    for {
        v, ok := <-ch
        if ok == false {
            break
        }
        fmt.Println("Received ", v, ok)
    }
}
```


##### Uni-Directional Channels

* Send-only channel: `sendch chan<- int`

* Uni-directional channels example:
```
package main

import "fmt"

func sendData(sendch chan<- int) {  
    sendch <- 10
}

func main() {  
    chnl := make(chan int)
    go sendData(chnl)
    fmt.Println(<-chnl)
}
```

Here, we convert bi-directional channel into a uni-directional channel

##### Buffered Channels and Worker Pools

* https://golangbot.com/buffered-channels-worker-pools/
