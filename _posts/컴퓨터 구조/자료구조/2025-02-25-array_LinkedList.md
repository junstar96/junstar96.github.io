---
layout : single
title : "array,list,vector"
author : 
name : 이준성
categories : review
tags : 컴퓨터 구조
toc : true
author_profile : false
sidebar:
    nav : "docs"

---

![배열과리스트](/assets/images/array_and_linkedList.png)

# 배열(array)

기본 정의 : 연관된 데이터를 모아서 관리하기 위한 데이터 타입. 한 가지 타입의 변수를 여러 개 동시에 저장해야 할 때 사용된다.<br>

> ## 특징
> 1. 연속적인 메모리 공간에 저장되는 자료 구조.
> 2. 배열의 크기는 고정되어 있으며 선언 시에 크기를 지정해야 한다.

```c
int arr[4];
```

# 리스트(list)

기본 정의 : 데이터를 나란히 저장하고 중복된 데이터의 저장을 막지 않는 자료 구조.<br>

> ## 특징
> 1. 원소의 개수가 가변적이다.
> 2. 삽입과 삭제가 자유롭다.

```c
#include <iostream>
#include <list>

int main() {
    std::list<int> numbers = {1, 2, 3, 4, 5};

    for (int number : numbers) {
        std::cout << number << std::endl;
    }
    return 0;
}
```

![링크드리스트](/assets/images/linkedlist.png)

## 링크드리스트

> 연결리스트라고도 불리며 떨어진 곳에 존재하는 데이터들을 연결하는 데이터 구조<br>
> ### 핵심 요소
> 1. 노드 : 연결리스트의 기본 단위로서 데이터를 저장하는 데이터 필드와 다음 노드를 가리키는 링크 필드로 구성된다.
> 2. 포인터 : 각 노드 안에서 다음이나 이전의 노드와의 연결 정보를 가지고 있는 공간<br>
> 3. 헤드 : 연결 리스트에서 제일 처음 위치하는 노드.
> 4. 테일 : 연결 리스트에서 제일 마지막에 위치하는 노드. 보통 시작했을 때는 헤드와 테일이 같은 것을 가리킨다.



# 벡터

배열과 비슷하나 초기 크기를 설정한 뒤에도 데이터를 추가할 수 있다. (배열과 리스트를 섞은 느낌)<br>


