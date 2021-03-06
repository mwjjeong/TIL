---
layout: default
title: Array
parent: Basics
grand_parent: Go
nav_order: 8
---
# Array
## Basics
* 정의 방법은 다음과 같다.
    ```go
    var 변수명 [개수]타입

    //Example
    var yourArr [10]int
    ```
* 다음과 같은 방식으로 초기화 할 수 있다.
    * 기본 방식
        ```go
        var yourArr [10]int = [10]int{1, 2, 3, 4, 5}
        ```
      * 초기화 하지 않는 경우 각 type의 기본값으로 초기화된다.
    * 배열의 길이보다 부족한 개수만큼 초기값이 명시되는 경우 남은 값은 기본값으로 초기화된다.
        ```go
        var yourArr [5]int = [5]int{5, 4}
        // 5 4 0 0 0
        ```
    * 다음과 같이 index 별로 specific 하게 초기값을 지정할 수 있다.
        ```go
        var yourArr [5]int = [5]int{1: 10, 3: 7}
        // 0 10 0 7 0
        ```
        * 지정되지 않은 다른 index의 값은 기본값으로 초기화된다.
    * 위의 변수명 뒤에 오는 type 명시는 생략 가능하다.
        ```go
        var yourArr = [5]int{1, 2, 3, 4, 5}
        ```
    * `...`로 배열의 개수 명시를 생략할 수 있다. 배열의 길이는 명시된 요소의 길이와 같다.
        ```go
        yourArr := [...]int{1, 2, 3}
        // Length: 3
        ```
* 배열의 개수는 **항상 상수로** 명시되어야 한다. 변수로 길이 지정할 수 없다.
* 배열의 element를 읽고 쓰는 방법은 다른 언어와 동일하다.

## Iteration
* 다음과 같이 `range` 를 이용해 iteration이 가능하다.
    ```go
    var yourArr = [...]int{3, 2, 1}

    for i, n := range yourArr {
        fmt.Println(i, n)
    }

    // 0 3
    // 1 2
    // 2 1
    ```
    * Iteration을 돌면서 총 두 개의 값을 받는데, 앞의 값은 index, 뒤의 값은 요소의 값이다.

* Index가 필요 없는 경우 다음과 같이 `_`를 이용해 무효화 하자.
    ```go
    for _, n := range yourArr {
        ...
    }
    ```

## Memory 상에 저장되는 방식
* 배열의 각 요소는 메모리 상에서 연속적으로 나열된 상태로 저장된다. (연속된 메모리이다.)
* Index와 type의 크기로 특정 요소의 메모리 주소를 찾는다.
* 대입 연산자 `=`로 배열의 복사가 가능하다. 이 때 각 요소의 type 및 배열의 길이는 같아야 한다.
    ```go
    a := [...]int{1, 1, 1}
    b := [...]int{2, 2, 2}
    b = a
    ```
## 다중 배열
* 배열의 배열이라고 생각하자!
    * e.g. [2][5]int 는 [5]int 라는 type에 대한 길이 2의 배열이다.
    * 배열의 배열의 배열 ... 또는 그 이상이 될 수도 있다.
    * 이와 같이 중첩된 배열이 있을 때 중첩된 정도를 **차원**이라 일컫는다.
* **[개수]타입** 임을 항상 명심하자.
* 이중 배열의 경우 다음과 같이 초기화 할 수 있다.
    ```go
    arr := [2][5]int{
        {5, 4, 3, 2, 1},
        {1, 2, 3, 4, 5},
    }
    ```
    * 배열의 마지막 요소와 `}`가 같은 줄에 있지 않은 경우 마지막 요소 뒤에 `,`를 붙여줘야 한다.
