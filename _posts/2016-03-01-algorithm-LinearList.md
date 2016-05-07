---
layout: blog
title:  "알고리즘 - 선형 리스트(Linear List)"
date:   2016-03-01
categories: blog
---
# 1. 선형 리스트(Linear List)
자료구조의 기본 표현방식인 선형 리스트를 익힌다.


# 1.1. 정의
- 원소들 간의 논리적인 순서와 메모리에 저장하는 물리적인 순서가 같은 순차 자료구조 방식이다.
- 원소들이 순서대로 연속하여 저장된다.
- 대표적으로 배열이 있다. <index, element>로 표현된다.

선형 리스트의 장점(연결 리스트와 비교했을 때)

- 논리적 순서 = 물리적 순서 -> 접근속도(access time)가 빠르다.
- 알고리즘이 간단하다.

선형 리스트의 단점(연결 리스트와 비교했을 때)

- 원소의 개수가 많고, 삽입/삭제 연산이 빈번할 경우 오버헤드가 증가 -> 성능상 문제를 야기한다.
- 초기에 배열의 크기를 정해야함 -> 메모리 사용이 비효율적이다.

# 1.2. 구현

{% highlight java %}
import java.util.Scanner;
public class LinearList_ex1 {

	public static void main(String[] args) {

		System.out.println("선형리스트 예제1 : 1차원 배열 ");

		int size;

		Scanner input = new Scanner(System.in);
		System.out.print("배열의 크기를 입력하시오: ");
		size = input.nextInt();

		int sale[] = new int[size];

		for (int i=0 ; i<sale.length ; i++){
			System.out.print("판매량을 입력하시오 : ");
			sale[i] = input.nextInt();
			}

		for (int i=0 ; i<sale.length ; i++) {
			System.out.printf("%d/4분기 : sale[%d] = %d %n", i+1, i, sale[i]);
		}
	}
}
{% endhighlight %}












