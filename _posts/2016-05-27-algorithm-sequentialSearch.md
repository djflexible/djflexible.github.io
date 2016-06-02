---
layout: blog
title:  "알고리즘 - 순차 검색(Sequential Search)"
date:   2016-05-25
categories: blog
---

목표
- 자료를 검색하는 순차검색에 대해 알아보고 구현해본다.

# 1. 순차 검색의 정의

- 일렬로 되어있는 자료를 처음부터 마지막까지 순서대로 검색하는 방법
- 장점 : 구현이 간단하다.
- 단점 : 자료의 양이 많을 경우 비효율적이다.


# 2. 순차 검색의 방법

- 순차 검색에서 비교횟수는 찾고자 하는 원소의 위치에 따라 다르다.
- 평균 시간복잡도는 O(n)
- 주어진 자료가 정렬이 되어있는 경우와 되어있지 않은 경우를 나눠서 생각한다.

# 2.1 정렬이 되어있는 순차 자료구조에서의 순차검색

- 첫 번째 원소부터 시작하여 마지막 원소까지 순서대로 key값이 일치하는 원소가 있는지를 비교하여 찾는다.
- key값이 일치하는 원소를 찾으면 그 원소가 몇 번째 원소인지를 반환한다.
- 원소의 key값이 찾는 key값보다 크면 찾는 원소가 없으므로 더 이상 검색을 수행하지 않고 끝낼 수 있다.


# 2.2 정렬이 되어있는 않은 순차 자료구조에서의 순차검색

- 첫 번째 원소부터 시작하여 마지막 원소까지 순서대로 key값이 일치하는 원소가 있는지를 비교하여 찾는다.
- key값이 일치하는 원소를 찾으면 그 원소가 몇 번째 원소인지를 반환한다.
- 마지막 원소까지 비교하여 key값이 일치하는 원소가 없으면 검색 실패가 된다.
- 검색 실패는 마지막 원소까지 모두 비교한 후에 알 수 있다.

# 3.1 구현

- 자료가 정렬되어 있는 경우와 정렬되어 있지 않은 경우에 대해 각각 구현해본다.


SequentialSearch.java

{% highlight java %}

public class SequentialSearch {

	private int i = 0;

	public void sequentialSearch1(int a[], int size, int key) { // 자료가 정렬되어 있지 않은 경우


		System.out.printf("\n %d를 순차검색 =>", key);

		while (i < size && (a[i] != key))
			i++;

		if (i < size)
			System.out.printf(" %d 번째에서 검색 성공 \n", i + 1);

		else
			System.out.printf(" %d 번째에서 검색 실패 \n", i + 1);
	}

	public void sequentialSearch2(int a[], int size, int key) { // 자료가 정렬되어 있는 경우

		System.out.printf("\n %d를 순차검색", key);

		while (a[i] < key)
			i++;

		if (a[i] == key)
			System.out.printf(" %d 번째에서 검색 성공 \n", i + 1);

		else
			System.out.printf(" %d 번째에서 검색 실패 \n", i + 1);

	}
}

{% endhighlight %}


SequentialSearch_test.java

{% highlight java %}

import java.util.Arrays;

public class SequentialSearch_test {

	public static void main(String[] args) {

		SequentialSearch search1 = new SequentialSearch();
		int a1[] = { 8, 30, 1, 9, 11, 19, 2 };
		int size = a1.length;

		System.out.printf("\n정렬되지 않은 자료에서의 순차 검색 "+ Arrays.toString(a1));
		search1.sequentialSearch1(a1, size, 9);
		search1.sequentialSearch1(a1, size, 32);

		/////////

		SequentialSearch search2 = new SequentialSearch();
		int a2[] = { 1, 2, 8, 9, 11, 19, 29};
		size = a2.length;

		System.out.printf("\n정렬되어 있는 자료에서의 순차 검색" + Arrays.toString(a2));
		search2.sequentialSearch2(a2, size, 9);
		search2.sequentialSearch2(a2, size, 10);

	}
}

{% endhighlight %}


참고문헌

책 - '자바로 배우는 쉬운 자료구조'

update : 2016-05-25