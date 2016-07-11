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
		- if elem, ok = m[key]; ok {} 로 사용할 수 있다.

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
- string empty check
	- if len(s) > 0 { ... } [ref](http://stackoverflow.com/questions/18594330/the-best-way-to-test-for-an-empty-string-in-go)
	
## Function
- Function is Full closures

## Method
- Method receiver
- 기본적으로 인터페이스에서 사용되는 메소드는 정의해두자.
	- fmt로 출력할 때 : String() string
	- error interface : Error() string

## Interface
- 여러 Method를 묶어 하나의 Interface로 만들 수 있다.(http://go-book.appspot.com/interfaces.html)

## File I/O
```go
import (
	"bufio"
	"os"
	"fmt"
)

func main() {
	f, _ := os.Open(path)
	scanner := bufio.NewScanner(f)

	for scanner.Scan() {
		line := scanner.Text()
		fmt.Println(line)
    }
}
```

## Concurrency
- Go routine
- Channels
	- `ch := make(chan int)`
	- 채널 송/수신은 준비될 때까지 블록됨 -> 명시적인 lock없이 동기화 가능
	- `i := range c` 처럼 쓰기 위해서는 채널을 close해야 함
		- `v, ok := <-ch` 채널이 닫히면 ok == false
- Select
	- 다수의 통신 동작으로부터 수행 준비 select-case
	- default는 수행 준비가 완료된 케이스가 없을 때 동작