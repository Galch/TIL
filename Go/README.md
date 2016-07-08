# study of [Go Programming Language](https://golang.org/)
Golang study

- 기본적인 문법 및 언어 설계 방법론은 하루 1시간 정도 공부
	- https://go-tour-kr.appspot.com/#1 
	- [Go Wiki](https://github.com/golang/go/wiki)
	- [Effective Go](https://golang.org/doc/effective_go.html)   
	- [Go 프로그래밍 입문](http://codingnuri.com/golang-book/)
	- [Rob Pike - ‘Concurrency Is Not Parallelism’](https://www.youtube.com/watch?v=cN_DpYBzKso)

### Goal
1. Go로 Embedded Application 작성 및 구동
2. Parallelism & Concurrency
 
### How to acheive
1. 복잡한 어플리케이션을 그냥 개발 후 크로스컴파일해서 ARM 기반 임베디드 시스템상에서 구동
	1. 통신 + 영상 처리 + 제어 알고리즘 + 포트 제어(?의존성) 정도?..
	1. Reference 
		- https://github.com/golang/go/wiki/GoArm
		- http://embd.kidoman.io/
		- http://dave.cheney.net/2015/09/04/building-go-1-5-on-the-raspberry-pi
2. 다양한 알고리즘 문제들 Go로 풀어보기
	1. [Hacker Rank](https://www.hackerrank.com/) 에서 Go로 연습
	1. [Project Euler](https://projecteuler.net/) Go로 풀이