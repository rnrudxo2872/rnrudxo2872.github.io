---
date: 2021-07-16
title: "[Go] slice와 struct"
categories:
  - Go
  - 문법
tags:
  - Go
  - 언어
  - 문법
---

## slice란?

Go에서 배열은 Javascript나 Python같이 동적인 배열선언은 할 수 없다고 앞서 포스팅했었다. 그럼 어떻게 동적인 배열을 만들까?  
**slice**라는 것을 사용하면 된다.  
선언은 배열과 동일하다.

```go
func main() {
	sliceType := []string{"slice-1", "slice-2"}
}
```

<br>

#### - append

slice에 요소를 추가하려면 append로 마지막에 추가할 수 있다.

```go
...
sliceType = append(sliceType, "slice-3", "slice-4")
```

<br>

#### - prepend

slice에서 아쉽게도 prepend는 존재하지 않는다. 하지만 비슷하게 구현할 수는 있다.

```go
...
sliceType = append([]string{"testFirst"}, sliceType...)
```

<br>

#### - remove

remove에 대한 함수도 따로 구현되어 있지 않은거 같았다.
그래서 임의적으로 구현해 본 결과.

```go
sliceType = append(sliceType[:3], sliceType[4:]...)
```

index가 3인 요소를 제거하는 과정이다. 프로젝트에서 사용할 때는 함수로 만들어 관리해도 좋을거 같다.
