---
layout: post
title:  "selection sort!"
---

#선택 정렬

1. 선택 정렬 알고리즘 동작 방법

- 가정: 정렬되지 않은 숫자들이 들어 있는 리스트와 정렬이 완료된 숫자들이 들어있는 리스트가 있다. 그림과 같이 초기 상태에서 정렬된 리스트는 비어 있고 정렬되어야 할 숫자들은 모두 오른쪽 리스트에 들어 있다. 선택 정렬은 오른쪽 리스트에서 가장 작은 숫자를 선택하여 오른쪽 리스트에서 가장 작은 숫자를 선택하여 왼쪽 리스트로 이동하는 작업을 반복한다.  이것은 오른쪽 리스트가 공백 상태가 될 때까지 되풀이 된다.

![image](https://user-images.githubusercontent.com/101514626/166663876-4892a3ec-9ec8-44de-a3ef-0be8dcffe410.png)

처음에는 두 개의 리스트로 나누어 설명했지만 실제로 선택 정렬을 구현하기 위해 두 개의 배열을 사용할 필요는 없다. 아래 그림과 같이 정렬이 안 된 리스트에서 최솟값이 선택되면 이 값을 배열의 첫번째 요소와 교환한다. 이렇게 입력 배열 이외에 다른 추가 메모리를 요구하지 않는 정렬 방법을 제자리 정렬(in-place sorting)이라고 한다. 최솟값 1과 첫 번째 요소 5를 교환하면 전체 배열은 정렬된 부분과 되지 않은 부분으로 나뉜다. 다음에는 두 번째 요소부터 나머지 요소들 중에서 가장 작은 값을 선택하고 이를 두 번째 요소와 교환한다. 이 절차를 (숫자 개수 -1)만큼 되풀이하면 추가적인 배열을 사용하지 않고서도 전체 숫자들이 정렬된다.

![image](https://user-images.githubusercontent.com/101514626/166664495-9f492420-199f-49b4-954f-dd6b406ff819.png)


2. 선택 정렬 알고리즘 구현

#include <iostream>
  

using namespace std;

  
inline void swap(int& x, int& y)

  {

  int t = x;
	
  x = y;
	
  y = t;

  }

  
void selectionSort(int a[], int n[])

  {
	
  for (int i = 0; i < n - 1; i++)
	
                       {
		int least = i;

                       for (int j = i + 1; j < n; j++)
		
  {
	
  if (a[j] < a[least])
	
                      least = j;
		
                      }
		
                      swap(a[i], a[least]);
	
                      }

                      }

                      

                      int main()

                      {
	
                      int arr[] = { 2, 7, 5, 1, 3, 9  };

                      
	
                      for (int i = 0; i < 6; i++)
		
  count << arr[i] << " ";
	
  count << end1;

  
	return 0;

  }
