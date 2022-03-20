---
layout: post
title:  "분할-정복법(divide and conquer)"
---

#퀵 정렬(Quick Sort) 

퀵 정렬(quick sort)
퀵 정렬은 분할-정복법(divide and conquer)에 근거하고 평균적으로 매우 빠른 수행 속도를 자랑하는 정렬 방법이다.
퀵 정렬은 합병정렬과는 다르게 리스트 안에 있는 한 요소를 피봇(pivot)으로 선택한다. 피봇보다 작은 요소들은 모두 피봇의 왼쪽으로 옮겨지고 피봇보다 큰 요소들운 모두 피봇의 오른쪽으로 옮겨진다. 이 상태에서 피봇을 제외한 왼쪽 리스트와 오른쪽 리스트를 다시 정렬하게 되면 전체 리스트가 정렬된다.

Q. 퀵 정렬은 어떻게 피봇을 기준으로 나누어진 왼쪽 부분 리스트와 오른쪽 부분 리스트를 정리할까?
A. 합병 정렬과 마찬가지로 퀵 정렬 함수가 다시 부분 리스트에 대하여 순환 호출된다. 

여기서 부분 리스트에서도 다시 피봇을 정하고 피봇을 기준으로 2개의 부분 리스트로 나누는 과정이 되풀이 된다. (부분 리스트들이 더 이상 분할이 불가능할 때까지 나누어진다.)

피봇 선정 방법 
• 랜덤하게 선정하는 방법
• 3 숫자의 중앙값으로 선정하는 방법(Median of Three): 가장 왼쪽 숫자, 중간 숫자, 가장 오른쪽 숫자 중에서 중앙값으로 피봇을 정한다.
• 중앙값들 중의 중앙값(Median of Medians): 입력을 3등분하여 각 부분에서 3 숫자의 중앙값을 찾아서 3개의 중앙값리서 중앙값으로 피봇으로 삼는다.


※ {1, 8, 5, 7, 3, 6, 9}을 퀵 정렬로 정렬 시키기

----------------------------------- 소스 코드 -----------------------------------
#include <stdio.h>

int number = 7;
int data[] = {1, 8, 5, 7, 3, 6, 9};

void show() {
	int i;
	for (i = 0; i < number; i++) {
		printf("%d", data[i]);
	}
}

void quickSort(int* data, int start, int end) {
	if (start >= end) {	//원소가 1개인 경우 그대로 두기
		return;
	}

	int key = start;	//키는 첫 번째 원소
	int i = start + 1, j = end, temp;

	while (i <= j) {	//엇갈릴 때까지 반복
		while (i <= end && data[i] <= data[key]) {	//키 값보다 큰 값을 만날 때까지
			i++;
		}
		while (j > start && data[j] >= data[key]) {	//키 값보다 작은 값을 만날 때까지
			j--;
		}
		if (i > j) {	//현재 엇갈린 상태면 키 값과 교체
			temp = data[j];
			data[j] = data[key];
			data[key] = temp;
		}
		else {	//엇갈리지 않았다면 i와 j를 교체
			temp = data[i];
			data[i] = data[j];
			data[j] = temp;
		}
	}


	quickSort(data, start, j - 1);
	quickSort(data, j + 1, end);
}

int main(void) {
	quickSort(data, 0, number - 1);
	show();
	return 0;
}
