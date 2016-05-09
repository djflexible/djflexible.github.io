---
layout: blog
title:  "자료구조 - 큐(Queue)"
date:   2016-03-05
categories: blog
---
# 큐(Queue)
단순 연결 리스트로 구현하는 큐를 만들어 본다.

# 1. 개념
- queue는 ‘줄’이라는 의미이다. 버스를 기다리는 사람들의 줄을 예로들 수 있다.
- 먼저 삽입된 데이터가 먼저 삭제되는 선입선출(FIFO, First In First Out)의 구조이다.


큐의 동작 용어

![linkedqueue1](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/dataStructure/linkedqueue1.png)

- rear : 저장된 원소 중 마지막 원소, 삽입 연산을 수행
- front : 저장된 원소 중 첫 번째 원소, 삭제 연산을 수행
- enQueue : 데이터를 삽입하는 연산, rear에서 이루어짐
- deQueue : 데이터를 삭제하는 연산, front에서 이루어짐, front=rear일 경우 빈 큐를 의미
- peek : front가 가리키는 데이터를 읽는 작업



# 2. 구현
- 큐를 구현하는 방법은 배열을 사용하는 순차 자료구조 방식과 참조변수를 사용하는 연결 자료 구조 방식이 있다.


순차 자료구조 방식을 이용하면 발생하는 문제점들


- 사용 크기가 제한되어 큐의 길이를 마음대로 변경할 수 없음(Circular Queue로도 해결 가능)
- 사용하지 않는 공간이 생길 경우 메모리가 낭비됨
- 위의 문제점을 해결하기 위해 단순 연결 리스트를 이용하여 큐를 구현한다.

![linkedqueue2](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/dataStructure/linkedqueue2.png)

단순 연결리스트로 구현한 큐의 그림

LinkedQueue.java

{% highlight java %}
public class LinkedQueue {

	private Node front;	//첫번째 node
	private Node rear;	//마지막 node
	private int size = 0;	//큐의 크기

	private class Node{
		private Object data;	//node의 데이터
		private Node nextNode;	//다음 node를 가리킴

		Node(Object data){	//마지막 node
			this.data = data;
			this.nextNode = null;
		}
	}

	public LinkedQueue(){	//큐 생성자
		this.front = null;
		this.rear = null;
	}

	public boolean empty(){	//큐가 비어있는지 확인
		return (front==null);
	}

	public void enQueue(Object input){ //데이터 삽입
		Node node = new Node(input);
		node.nextNode = null;

		if(empty()){
			rear = node;
			front = node;
		}else{
			rear.nextNode = node;
			rear = node;
		}
		size++;
	}

	public Object peek(){	//front의 데이터 반환
		if(empty()){
			throw new ArrayIndexOutOfBoundsException();
		}
			return front.data;
		}

	public Object deQueue(){	//front를 큐에서 삭제
		Object input = peek();
		front = front.nextNode;

		if(front ==null){
			rear =null;
		}
		size--;
		return input;
	}

	public String toString(){	//큐 출력
		if(front == null){
			return "[]";
		}
		else{
			Node temp = front;
			String str = "[";

			while(temp.nextNode != null){
				str += temp.data + ", ";
				temp = temp.nextNode;
			}
			str += temp.data;
			return str+"]";
		}
	}
	public int size(){	//큐의 크기
		return size;
	}
}
{% endhighlight %}


LinkedQueue_Test.java

{% highlight java %}
public class LinkedQueue_Test {

	public static void main(String[] args) {

		LinkedQueue linkedQueue = new LinkedQueue();
		System.out.println("LinkedQueue 테스트");

		for(int i=1 ; i<=5 ; i++){
			linkedQueue.enQueue(i);
		}
		System.out.println(linkedQueue);
		System.out.println("size : "+linkedQueue.size());

		System.out.println("deQueue 실행 : "+ linkedQueue.deQueue() +" 삭제");
		System.out.println(linkedQueue);
		System.out.println("size : "+linkedQueue.size());
	}
}
{% endhighlight %}

# 참고문헌

[itdexter][itdexter]님, [songeunjung92][songeunjung92]님, 책 - '자바로 배우는 쉬운 자료구조'

[itdexter]: http://itdexter.tistory.com/79
[songeunjung92]: http://songeunjung92.tistory.com/23

update : 2016-03-05