Basics
========

- Pros
	- go fmt 등으로 코딩 스타일을 강제하여 전체 소스 일관성 유지
	- go routine

## Data Types

### [big.Int](http://stackoverflow.com/questions/30182129/calculating-large-exponentiation-in-golang)
BigInt package allows you to calculate x^y in log time (for some reason it is called exp). All you need is to pass nil as a last parameter.
큰 수를 빠르게 연산할 때 필요

### 2d Slice
2d slice 는 append를 이용하여 한 줄씩 할당할 수 있다.

```go
func something(dx, dy int) [][]uint8 {
    result := [][]uint8{}
    
    for y := 0; y < dy; y++ {
        row := make([]uint8,dx)
        for x := 0; x < dx; x++ {
        	row[x] = uint8(x * y)
        }
        result = append(result,row)
    }    
    return result
}
```

### Map
무조건 make를 명시해야함
- Mutating Maps
	- m := make(map[string]int)
	- m[key] = elm
	- elem = m[key]
	- delete(m, key)
	- elem, ok = m[key]

### String

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

## Function
- Function is Full closures
```go
func adder() func(int) int {
    sum := 0
    return func(x int) int {
        sum += x
        return sum
    }
}
``` 

### Interface
다른 클래스에 같은 기능이 있을 경우 interface로 묶는 개념, 상속과는 다르다

```go
import "fmt"
 
type Cat struct {
}
 
type Dog struct {
}
 
func (c Cat) Sound() {
    fmt.Println("냐옹")
}
 
func (d Dog) Sound() {
    fmt.Println("멍멍")
}
 
type Animal interface {
    Sound()
}
 
func main() {
    var animal1 Animal
    var animal2 Animal
 
    animal1 = Cat{}
    animal2 = Dog{}
 
    animal1.Sound();
    animal2.Sound();
}
```
