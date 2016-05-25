---
layout: blog
title:  "알고리즘 - 삽입정렬(Insertion sort)"
date:   2016-05-24
categories: blog
---
목표

- 삽입정렬의 방법을 알아보고 구현해본다.

# 1. 삽입정렬 알고리즘

# 1.1. 알고리즘 설명

- 삽입을 이용한 정렬 알고리즘
- 무엇을 삽입하는가? -> key값과 정렬된 리스트가 주어졌을 때 key값을 정렬된 리스트의 알맞은 위치에 삽입

ex)  A[5, 2, 4, 6, 1, 3]이 주어진 배열이라고 할 때

- 1 step　- 첫 번째 리스트는 이미 정렬되어 있으므로 두 번째 리스트부터 시작한다.
- 2 step　- 두 번째 리스트와 첫 번째 리스트를 비교하여 정렬한다.
- 3 step　- 세 번째 리스트와 이전 단계까지 정렬되어 있는 리스트를 비교하여 정렬한다.
- 4 step　- 위의 과정을 반복하여 n 번째 리스트와 n-1번째 단계까지 정렬되어 있는 리스트를 비교하여 정렬한다.

![insertion](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/algorithm/insertionSort.png)


# 1.2. 성능 분석

- 최선의 경우 : O(n), 입력받은 배열이 이미 정렬이 되어 있는 경우 -> 리스트가 추가될 때마다 바로 앞의 리스트하고만 비교(1번)하기 때문
- 최악의 경우 : O(n^2), 입력받은 배열이 정렬하고자 하는 방법의 역순일 경우 -> 리스트가 추가될 때마다 앞의 모든 리스트와 비교하기 때문 ex) 오름차순으로 정렬된 배열을 내림차순으로 정렬할 때
- 평균의 경우 : O(n^2)
- 공간 복잡도 : 제자리 정렬(sorted in place)로 추가 공간을 사용하지 않는다.

# 1.3. 구현
- java를 이용하여 구현해 본다.

InsertionSort.java

{% highlight java %}

public class InsertionSort {

	private int i;
	private int j;
	private int t;
	private int temp;

	public void insetrionSort(int a[], int size) {

		for (i = 1; i < size; i++) {

			temp = a[i];
			j = i;

			while ((j > 0) && (a[j - 1] > temp)) {
				a[j] = a[j - 1];
				j--;
			}

			a[j] = temp;
			System.out.printf("\n삽입정렬 %d 단계 : ", i);

			for (t = 0; t < size; t++) {
				System.out.printf("%3d", a[t]);
			}
			System.out.println();
		}
	}
}

{% endhighlight %}


InsertionSort_test.java

{% highlight java %}

public class InsertionSort_test {

	public static void main(String[] args) {

		int a[] = {5, 2, 4, 6, 1, 3};
		int size = a.length;

		InsertionSort sort = new InsertionSort();

		System.out.println("삽입 정렬");
		System.out.printf("\n정렬할 원소 : ");

		for (int i = 0; i < a.length; i++)
			System.out.printf(" %d", a[i]);

		System.out.println();
		sort.insetrionSort(a, size);

	}
}

{% endhighlight %}

참고문헌


[T아카데미 조호성][T아카데미 조호성]님, [위키백과][위키백과], 책 - '자바로 배우는 쉬운 자료구조'

[T아카데미 조호성]: https://tacademy.sktechx.com/live/player/listOnline.action#
[위키백과]:https://ko.wikipedia.org/wiki/%EC%82%BD%EC%9E%85_%EC%A0%95%EB%A0%AC


update : 2016-05-24