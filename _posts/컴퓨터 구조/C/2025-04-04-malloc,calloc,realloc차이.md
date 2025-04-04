---
layout : single
title : "C/C++"
author : 
name : 이준성
categories : review
tags : 컴퓨터 구조
toc : true
author_profile : false
sidebar:
    nav : "docs"
---


# 기본 지식

> 프로그램을 실행시키면 운영체제는 우리가 실행시킨 프로그램을 위해 메모리 공간을 할당해준다. <br>
> 할당되는 공간은 크게 스택(stack),힙(heap),데이터(data)영역으로 나뉘어진다.<br>

> 1. 데이터 영역
> - 전역 변수와 static 변수가 할당되는 영역
> - 프로그램의 시작과 동시에 할당되고 프로그램이 종료되어야 메모리에서 소멸
> 2. 스택 영역
> - 함수 호출 시 생성되는 지역 변수와 매게 변수가 저장되는 영역
> - 함수 호출이 완료되면 사라짐
> 3. 힙 영역
> - 필요에 의해 동적으로 메모리를 할당할 때 사용(event 방식이 이 쪽으로 보임)



# malloc 함수

- 동적으로 메모리를 할당하는 함수<br>
- malloc은 단순히 메모리만 할당하는 함수이기에 개발자가 어떤 데이터 형을 저장하는지 예측할 수 없다. 그렇기에 나중에 알맞는 용도로 변한항 사용할 수 있도록 만듦<br>
- 나중에 변환할 수 있다.

```c
#include <stdlib.h>
#include <stdlib.h>

void main()
{
    int arr_1[5];
    int *arr_2;
    int i;

    for(i = 0;i<5;i++)
    {
        arr_1[i] = i+1;
    }

    arr_2 = (int*) malloc(sizeof(int)*5);

    for(i = 0;i<5;i++)
    {
        arr_2[i] = arr_1[i];
    }

    free(arr_2);
}
```


# calloc 함수
기본적으로 malloc 함수와 같은 기능을 가지고 있으나 사용 형태가 조금 다르다. malloc에서 모든 공간의 값을 0으로 초기화 할 때 calloc을 쓴다.

# realloc 함수
이미 할당된 공간의 크기를 바꿀 때 사용함.

```c
#include <stdlib.h>

void* realloc(void* memblock, size_t size);	// realloc 함수의 원형

이미 할당한 포인터 변수를 memblock에 넣고, 바꾸고 싶은 공간의 크기를 size에 입력하여 사용한다.

realloc함수 사용 예
malloc함수를 사용한 예제에서 realloc 함수를 사용하여 변경하였다.

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
	int arr_1[10];	// 배열 선언
	int *arr_2;		// 포인터 변수 선언
	int i;

	for(i = 0; i < 10; i++) {
		arr_1[i] = i+1;	// 배열에 값 대입
	}

	arr_2 = (int*) malloc(sizeof(int)*5);	// 메모리 할당, 배열의 크기만큼 할당하기 위해 5를 곱함

	for(i = 0; i < 5; i++) {
		arr_2[i] = arr_1[i];
		printf("%d ", arr_2[i]);
	}

	printf("\n");

	// sizeof(int) = 4바이트
	realloc(arr_2, sizeof(int)*10);	// arr_2의 메모리를 40바이트로 재 할당
	// arr_2의 메모리 크기 : 20바이트 -> 40바이트

	for(i = 0; i < 10; i++) {
		arr_2[i] = arr_1[i];
		printf("%d ", arr_2[i]);
	}

	free(arr_2);	// free함수를 이용하여 메모리 해제

	return 0;
}
```