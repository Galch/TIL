Basics
========

## String

- [efficeient string concatence](http://stackoverflow.com/questions/1760757/how-to-efficiently-concatenate-strings-in-go)

```Go
package main

import (
    "bytes"
    "fmt"
)

func main() {
    var buffer bytes.Buffer

    for i := 0; i < 1000; i++ {
        buffer.WriteString("a")
    }

    fmt.Println(buffer.String())
}

BenchmarkConcat  1000000    64497 ns/op   502018 B/op   0 allocs/op
BenchmarkBuffer  100000000  15.5  ns/op   2 B/op        0 allocs/op
BenchmarkCopy    500000000  5.39  ns/op   0 B/op        0 allocs/op
```

### [big.Int](http://stackoverflow.com/questions/30182129/calculating-large-exponentiation-in-golang)
BigInt package allows you to calculate x^y in log time (for some reason it is called exp). All you need is to pass nil as a last parameter.
큰 수를 빠르게 연산할 때 필요
