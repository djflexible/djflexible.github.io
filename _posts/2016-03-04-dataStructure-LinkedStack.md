---
layout: blog
title:  "자료구조 - 스택(Stack)"
date:   2016-03-04
categories: blog
---
# 스택(Stack)
자료구조의 단순 연결리스트로 구현하는 스택을 만들어 본다.

# 1. 개념

- 스택(Stack)이란 쌓아 올린다는 의미이다.
- 시간순서에 따라 자료가 쌓이고, 삭제할 때는 가장 마지막에 삽입된 자료가 가장 먼저 삭제되는 후입선출(LIFO, Lirst In First Out)의 구조를 갖는다.


스택의 용어

- top : 가장 최근에 입력된 데이터. 삽입, 삭제, 읽기 기능을 수행
- push : top에 새로운 데이터를 삽입하는 연산
- pop : top에 있는 데이터를 제거하는 연산
- peek : top에 있는 데이터를 읽는 연산

스택에서 연산이 수행되는 과정

![linkedstack1](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/dataStructure/linkedstack1.png)


# 2. 구현

- 스택은 배열, 연결 리스트로 구현할 수 있다.
- 스택은 삽입/삭제 연산이 빈번하므로 연결 리스트로 구현해본다. -> LinkedStack
- 단순 연결 리스트로 스택 구현

LinkedStack.java

{% highlight java %}
public class LinkedStack {
	private Node top;
	private int size = 0;
	private class Node{
		private Object data; //node의 데이터
		private Node nextNode;	//다음 node를 가리킴

	Node(Object data){	//마지막 노드
		this.data = data;
		this.nextNode = null;
		}
	}

	public LinkedStack(){ //생성자
		this.top = null;
	}

	public boolean isEmpty(){ //스택이 비어있는지 확인
		return (top == null);
	}

	public void push(Object input){	//push 연산

		Node newNode = new Node(input);
		newNode.nextNode = top;
		top = newNode;
		size++;
	}

	public Object peek(){	//top 노드 반환

		if(isEmpty()){
			throw new ArrayIndexOutOfBoundsException();
		}
		return top.data;
	}

	public Object pop(){	//pop 연산
		Object input = peek();
		top = top.nextNode;
		size --;
		return input;
	}

	public String toString(){	//스택 출력
		if(top == null){
			return "[]";
		}
		else{
			Node temp = top;
			String str = "[";

			while(temp.nextNode != null){
				str += temp.data + ", ";
				temp = temp.nextNode;
			}
			str += temp.data;
			return str+"]";
		}
	}
	public int size(){	//스택의 크기
		return size;
	}
}

{% endhighlight %}


LinkedStack_Test.java
{% highlight java %}
public class LinkedStack_Test {

	public static void main(String[] args) {

		LinkedStack linkedStack = new LinkedStack();
		System.out.println("LinkedStack 테스트");

		for(int i=1 ; i<=5 ; i++){
			linkedStack.push(i);
		}
		System.out.println(linkedStack + " 스택의 크기 : " + linkedStack.size());
		linkedStack.pop();
		System.out.println(linkedStack + " 스택의 크기 : " + linkedStack.size());
	}
}
{% endhighlight %}

# 참고문헌

[guguru][guguru]님, [hyeonstorage][hyeonstorage]님, 책 - '자바로 배우는 쉬운 자료구조'

[guguru]: http://guguru.tistory.com/16
[hyeonstorage]: http://hyeonstorage.tistory.com/258

update : 2016-03-04












