---
layout: blog
title:  "알고리즘 - 해쉬 테이블(Hash Table)"
date:   2016-06-01
categories: blog
---

목표

- 자료를 검색하는 해쉬 테이블을 알아보고 구현해 본다.

# 1. 해쉬 테이블(Hash Table)

- 산술적인 연산을 이용해 key가 있는 위치를 계산하여 찾아가는 검색방식
- 해싱 함수에 의해 계산된 주소의 위치에 항목을 저장한 표를 해쉬 테이블이라 한다.
- JAVA Collection Framework의 상속 기본 구조 참고

![external](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/algorithm/collection_Framework.png)


# 1.2 해싱(Hashing) 함수

어떤 해싱 함수를 사용하느냐에 따라 해싱 검색의 효율이 달라진다. 다음은 좋은 해싱 함수의 조건이다.

- 해싱 함수는 계산이 쉬워야 함 : key값을 이용해 직접 검색하는 방법보다 해싱 함수를 이용하여 계산하는 시간이 빨라야 해싱 검색을 사용하는 의미가 있다.
- 해싱 함수는 충돌이 적어야 함 : 충돌이란 서로 다른 key값에 대해 해싱 함수에 의해 주어진 버킷 주소가 같은 경우를 말한다. 버킷 주소 안이 슬롯이 없을 경우 포화 버킷상태가 되어 overflow가 발생할 수 있다. overflow를 처리하기 위해 선형개방 주소법(해시 테이블 내에 비어있는 슬롯을 순차적으로 찾음), 체이닝(해시 테이블의 구조를 변경하여 각 버킷에 하나 이상의 key값을 저장할 수 있도록 함, 연결리스트 이용) 방법을 사용한다.
- 따라서 해시 테이블에 고르게 분포할 수 있도록 주소를 만들어야 한다.
- 해싱 함수의 종류 : 중간 제곱 함수, 제산 함수, 승산 함수, 접지 함수, 숫자 분석 함수, 진법 변환 함수, 비트 추출 함수 등이 있다.


# 1.3 해쉬 테이블의 장단점

- 장점 : Ditect-Address Table과 비교하면 공간 낭비를 적게 한다.
- 단점 : 한 개의 key값에 여러 개의 값이 저장되어 포화 상태가 될 경우 충돌이 발생한다.  => 체이닝을 사용하게 되어 시간 복잡도 증가
- Ditect-Address Table와 Hash Table의 저장 구조 참고
![external](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/algorithm/directAddressTable.png)
![external](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/algorithm/hashTable.png)

# 2.1 구현

- 자바에서 HashMap과 Hashtable을 이용해서 구현할 수 있다.
- HashMap : 동기화가 보장되지 않는다 > single thread에 적합
- Hashtable : 동기화가 보장된다 => multi thread에 적합
- [jpstory][jpstory]님의 'Hashtable과 HashMap, ConcurrentHashMap의 차이점' 글 참고


HashMap_test.java

{% highlight java %}

import java.util.HashMap;
import java.util.Iterator;

public class HashMap_test {

	public static void main(String[] args) {
		// 키 값이 문자
		HashMap<String, String> fruitMap = new HashMap();
		fruitMap.put("d레몬", "yellow");
		fruitMap.put("e사과", "red");
		fruitMap.put("b배", "white");
		fruitMap.put("c자두", "red");
		fruitMap.put("a수박", "green&black");

		System.out.println(fruitMap.get("a수박"));
		System.out.println(fruitMap.values());

		Iterator<String> iterator = fruitMap.keySet().iterator();

		while (iterator.hasNext()) {

			String key = (String) iterator.next();
			System.out.print("과일 = " + key);
			System.out.println(", 색깔 = " + fruitMap.get(key));
		}

		// 키 값이 숫자
		HashMap<Integer, String> fruitMap2 = new HashMap();
		fruitMap2.put(12, "red");
		fruitMap2.put(4, "red");
		fruitMap2.put(2, "yellow");
		fruitMap2.put(1, "white");
		fruitMap2.put(5, "green&black");

		System.out.println(fruitMap2.get(2));
		System.out.println(fruitMap2.values());

		Iterator<Integer> iterator2 = fruitMap2.keySet().iterator();

		while (iterator2.hasNext()) {

			int key = (Integer) iterator2.next();
			System.out.print("과일 = " + key);
			System.out.println(", 색깔 = " + fruitMap2.get(key));
		}
	}
}

{% endhighlight %}


참고문헌

[T아카데미 조호성][T아카데미 조호성]님, [vaert][vaert]님, [jpstory][jpstory]님,  책 - '자바로 배우는 쉬운 자료구조'

[jpstory]: http://www.jpstory.net/2013/11/difference-hashtable-hashmap-concurrenthashmap
[T아카데미 조호성]: https://tacademy.sktechx.com/live/player/listOnline.action#
[vaert]: http://vaert.tistory.com/107

update : 2016-06-01