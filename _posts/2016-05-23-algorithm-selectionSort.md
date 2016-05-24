---
layout: blog
title:  "알고리즘 - 선택정렬(Selection sort)"
date:   2016-05-23
categories: blog
---
목표

- 선택정렬의 방법을 알아보고 구현해본다.

# 1. 정렬문제 정의

- 입력(input) : n개의 숫자들의 배열
- 출력(output) : 조건에 만족하도록 다시 나열(오름차순, 내림차순)

# 2. 선택정렬 알고리즘

# 2.1. 알고리즘 설명

- 선택하여 정렬하는 알고리즘
- 무엇을 선택할 것인가? -> 최소값 or 최대값
- 최소값 선택정렬 : 가장 작은 값을 선택 -> 오름차순
- 최대값 선택정렬 : 가장 큰 값을 선택 -> 내림차순

단계) 최소값 선택정렬

- 1 step : 정렬되지 않은 숫자 중에서 가장 작은 숫자를 선택
- 2 step : 선택한 숫자를 현재 정렬되지 않은 숫자들 중 첫 번째 숫자와 자리를 바꿈
- 3 step : 모든 숫자가 오름차순으로 정렬될 때까지 1,2 과정을 반복

ex) 5, 2, 4, 6, 1, 3을 오름차순으로 정렬해본다.

![selection](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/algorithm/selectionSort.png)

- 마지막 남은 숫자는 정렬할 필요가 없다. n개를 정렬할 경우 n-1번 시행

# 2.3. 성능 분석

- 최선/최악의 경우 수행 시간 : O(n^2) -> 입력 받은 초기 배열의 상태와 관계없이 어떤 경우에서나 비교 횟수가 같다
- 최선/최악의 경우 공간 : O(n)
- 입력 받은 숫자들의 배열의 형태에 관계없이 수행 시간과 공간이 같기 때문에 최선/최악의 경우가 없다.

# 2.4. 구현
- java를 이용하여 구현해 본다.

SelectSort.java

{% highlight java %}

class SelectSort {

	private int i;
	private int j;
	private int min; // 정렬된 배열 중 최소값

	public void selectionSort(int a[]) {

		for (i = 0; i < a.length - 1; i++) {
			min = i;
			for (j = i + 1; j < a.length; j++) {
				if (a[j] < a[min])
					min = j;
			}

			swap(a, min, i);
			System.out.printf("\n 선택정렬 %d 단계 : ", i + 1);
			for (j = 0; j < a.length; j++)
				System.out.printf("%3d", a[j]);
		}
	}

	public void swap(int a[], int i, int j) {
		int temp = a[i];
		a[i] = a[j];
		a[j] = temp;
	}

}

{% endhighlight %}


SelectSort_test.java

{% highlight java %}

public class SelectSort_test {

	public static void main(String[] args) {

		System.out.println("선택 정렬");
		int a[] = { 5, 2, 4, 6, 1, 3 };
		// int a[] = {69, 10, 30, 2, 16, 8, 31, 22};

		SelectSort sort = new SelectSort();
		System.out.println("정렬할 원소 : ");

		for (int i = 0; i < a.length; i++)
			System.out.printf(" %d", a[i]);

		System.out.println();
		sort.selectionSort(a);

	}

}

{% endhighlight %}


참고문헌


[T아카데미 조호성][T아카데미 조호성]님, [위키백과][위키백과], 책 - '자바로 배우는 쉬운 자료구조'

[T아카데미 조호성]: https://tacademy.sktechx.com/live/player/listOnline.action#

[위키백과]:https://ko.wikipedia.org/wiki/%EC%84%A0%ED%83%9D_%EC%A0%95%EB%A0%AC

update : 2016-05-23