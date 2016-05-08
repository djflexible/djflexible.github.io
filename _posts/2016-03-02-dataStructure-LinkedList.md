---
layout: blog
title:  "자료구조 - 연결 리스트(Linked List)"
date:   2016-03-02
categories: blog
---
# 1. 연결 리스트(Linked List)
자료구조의 기본 표현방식인 연결 리스트를 익힌다.

# 1.1. 정의
- 자료들을 연결 구조 방식으로 표현한다.
- 각 원소에 저장되어 있는 다음 원소의 주소에 대한 참조에 의해 연결된다.
- 연결 리스트는 <element, address> 단위로 저장된다. 이러한 단위구조를 노드(node)라 한다. 노드는 데이터 필드와 링크 필드로 구성된다.
- 데이터 필드(Data field) : 저장할 원소의 값이다. 변수
- 링크 필드(Link field) : 메모리 참조 변수를 사용하여 주소에 대한 참조 값을 저장한다.
- 단순 연결리스트, 원형 연결리스트, 이중 연결리스트, 이중 원형 연결리스트가 있다.

연결 리스트의 장점(선형 리스트와 비교했을 때)

- 논리적 순서와 물리적 순서가 일지하지 않아도 됨 -> 오버헤드가 발생하지 않는다.
- 데이터를 삽입/삭제할 때 모든 인덱스를 변경하지 않고 이전 데이터에 대한 참조만 변경하면 된다.
- 크기 변경에 유연하여 효율적으로 메모리를 사용할 수 있다.

연결 리스트의 단점(선형 리스트와 비교했을 때)

- 접근속도(access time)에 많은 시간이 걸린다.
- 알고리즘이 복잡하다.

# 1.2. 구현

# 1.2.1. 단순 연결 리스트(Singly Linked List)

- 한쪽 방향으로만 연결된다.
- 생성, 삽입, 삭제, 탐색 구현

단순 연결 리스트의 기본 구조
![linkedlist2](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/dataStructure/linkedlist2.png)

{% highlight java %}
class LinkedList{
	private Node head;
	private Node tail;
	private int size = 0;

	private class Node{
		private Object data;	//node 값
		private Node next;		//참조 값(다음 node의 주소)
		public Node(Object input){
			this.data = input;
			this.next = null;
		}
		public String toString(){	//참조값을 data 값으로 변환
			return String.valueOf(this.data);
		}
	}

	public void addFirst(Object input){	// head부터 데이터 추가
		Node newNode = new Node(input);
		newNode.next = head;
		head = newNode;
		size++;
		if(head.next ==null){
			tail = head;
		}
	}

	public void addLast(Object input){	// tail부터 데이터 추가
		Node newNode = new Node(input);

		if(size==0){	//리스트에 노드가 없을 경우
			addFirst(input);
		}
		else{
			tail.next = newNode;
			tail = newNode;
			size++;
		}
	}

	Node findNode(int index){	//특정 위치의 노드를 찾음
		Node x = head;
		for(int i=0 ; i<index ; i++){
			x = x.next;
		}
		return x;
	}

	public void add(int k, Object input){	//중간에 데이터 추가
		if(k == 0){
			addFirst(input);
		} else{
			Node temp1 = findNode(k-1);
			Node temp2 = temp1.next;
			Node newNode = new Node(input);
			temp1.next = newNode;
			newNode.next = temp2;
			size++;
			if(newNode == null){
				tail = newNode;
			}
		}
	}

	public String toString(){	//연결 리스트 출력
		if(head == null){
			return "[]";
		}
		else{
			Node temp = head;
			String str = "[";

			while(temp.next != null){
				str += temp.data + ", ";
				temp = temp.next;
			}
			str += temp.data;
			return str+"]";
		}
	}

	public Object removeFirst(){	//head부터 삭제
		Node temp = head;
		head = head.next;
		Object returnData = temp.data;
		temp = null;
		size--;
		return returnData;
	}

	public Object remove(int k){	//중간 데이터 삭제
		if(k == 0){
			return removeFirst();
		}

		Node temp = findNode(k-1);
		Node deleteNode = temp.next;
		temp.next = temp.next.next;
		Object returnData = deleteNode.data;

		if(deleteNode == tail){	//삭제할 노드가 마지막일 경우
			tail = temp;
		}
		size--;
		return returnData;
	}

	public Object removeLast(){	//tail부터 삭제
		return remove(size-1);	//tail 바로 전을 알아야 한다. 가장 마지막 삭제는 최악의 경우
	}

	public int size(){	//엘리먼트의 크기
		return size;
	}

	public Object get(int k){	//특정 엘리먼트 값 가져오기
		Object returnData = findNode(k) ;
		return returnData;
	}

	public int indexOf(Object data){	//특정값 탐색
		Node temp = head;
		int index = 0;
		while(temp.data != data){
			temp = temp.next;
			index++;
			if(temp == null){
				return -1;
				}
		}
		return index;
	}
}

public class LinkedList_ex2 {

	public static void main(String[] args) {
		LinkedList numbers = new LinkedList();


		System.out.println("단순 연결 리스트");
		numbers.addFirst(40);
		numbers.addFirst(30);
		numbers.addFirst(20);
		numbers.addFirst(10);
		System.out.println(numbers);
		System.out.println("Let's go test");
	}
}
{% endhighlight %}

'중간에 데이터 추가' 참고 그림

![linkedlist3](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/dataStructure/linkedlist3.png)


# 참고문헌

[생활코딩][opentutorials]님, [hyeonstorage][hyeonstorage]님, 책 - '자바로 배우는 쉬운 자료구조'

[opentutorials]: https://opentutorials.org/module/1335/8857#entirecode
[hyeonstorage]: http://hyeonstorage.tistory.com/258

update : 2016-03-02












