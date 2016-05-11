---
layout: blog
title:  "자료구조 - 이진트리(Binary Tree)"
date:   2016-03-07
categories: blog
---
# 이진 트리(Binary Tree)
계층형 자료구조(Hierarchical Data Structure)인 이진 트리에 대해 알아본다. 이진트리의 순회와 이진 탐색트리를 만들어 본다.

# 1. 개념

이진 트리의 용어

- 깊이 : 루트노드에서 해당 노드까지의 경로의 길이
- 레벨 : 깊이가 같은 노드들의 집합
- 차수 : 해당 노드의 자식 노드의 수
- 길이 : 출발 노드에서 목적 노드까지의 거리

이진 트리의 종류

- 포화 이진 트리(Full Binary Tree)
- 완전 이진 트리(Complete Binary Tree)
- 편향 이진트리(Skewed Binary Tree)


![binarytree2](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/dataStructure/binarytree2.png)
![binarytree1](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/dataStructure/binarytree1.png)



# 2. 구현
배열을 이용한 방법과 연결 리스트를 이용한 방법이 있다. 배열을 이용할 경우 구현이 쉽고 인덱스 규칙에 따라 특정 노드를 찾기 쉽다. 하지만 자료가 편향 이진트리와 같은 구조일 경우 메모리 낭비가 심해진다. 따리서 연결 리스트를 이용해 구현해 본다.

![binarytree3](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/dataStructure/binarytree3.png)

# 이진 트리의 순회
현재 노드를 D, 왼쪽 노드를 L, 오른쪽 노드를 R이라 하면


- 전위순회 : DLR
- 중위순회 : LDR
- 후위순회 : LRD

LinkedBinaryTree.java

{% highlight java %}
class TreeNode {
	Object data;
	TreeNode left;
	TreeNode right;
}

public class LinkedBinaryTree {

	private TreeNode root;

	public TreeNode makeTree(TreeNode bt1, Object data, TreeNode bt2) {
		TreeNode root = new TreeNode();
		root.data = data;
		root.left = bt1;
		root.right = bt2;

		return root;
	}

	public void preorder(TreeNode root) {
		if (root != null) {
			System.out.printf("%c", root.data);
			preorder(root.left);
			preorder(root.right);
		}

	}

	public void inorder(TreeNode root) {
		if (root != null) {
			inorder(root.left);
			System.out.printf("%c", root.data);
			inorder(root.right);
		}

	}

	public void postorder(TreeNode root) {

		if (root != null) {
			postorder(root.left);
			postorder(root.right);
			System.out.printf("%c", root.data);

		}

	}

}
{% endhighlight %}

LinkedBinaryTree_Test.java

{% highlight java %}
public class LinkedBinaryTree_Test {

	public static void main(String[] args) {

		LinkedBinaryTree tree = new LinkedBinaryTree();

		// 이진 트리 생성
		TreeNode node7 = tree.makeTree(null, 'D', null);
		TreeNode node6 = tree.makeTree(null, 'C', null);
		TreeNode node5 = tree.makeTree(null, 'B', null);
		TreeNode node4 = tree.makeTree(null, 'A', null);
		TreeNode node3 = tree.makeTree(node6, '/', node7);
		TreeNode node2 = tree.makeTree(node4, '*', node5);
		TreeNode node1 = tree.makeTree(node2, '-', node3);

		System.out.printf("\n 전위순회 : ");
		tree.preorder(node1);

		System.out.printf("\n 중위순회 : ");
		tree.inorder(node1);

		System.out.printf("\n 후위순회 : ");
		tree.postorder(node1);

	}

}
{% endhighlight %}


# 이진 탐색 트리(Binary Search Tree)
- 모든 원소는 서로 다른 유일한 키를 갖는다.
- 왼쪽 서브 트리에 있는 원소의 키들은 그 루트의 키보다 작다.
- 오른쪽 서브 트리에 있는 원소의 키들은 그 루트의 키보다 작다.
- 왼쪽 서브 트리와 오른쪽 서브 트리도 이진 탐색 트리다.


BinarySearchTree.java

{% highlight java %}
class TreeNode {
	char data; // Object로 선언할 경우 비교 불가능
	TreeNode left;
	TreeNode right;
}

public class BinarySearchTree {
	private TreeNode root = new TreeNode();

	public TreeNode insertKey(TreeNode root, char input) {
		TreeNode p = root; // 참조변수
		TreeNode newNode = new TreeNode();
		newNode.data = input;
		newNode.right = null;
		newNode.left = null;

		if (p == null) {
			return newNode;

		} else if (newNode.data < p.data) {
			p.left = insertKey(p.left, input);
			return p;

		} else if (newNode.data > p.data) {
			p.right = insertKey(p.right, input);
			return p;
		}

		else
			return p;

	}

	public void insertBST(char input) {
		root = insertKey(root, input);
	}

	public TreeNode searchBST(char input) {
		TreeNode p = root;
		while (p != null) {
			if (input < p.data)
				p = p.left;

			else if (input > p.data)
				p = p.right;
			else
				return p;
		}
		return p;
	}

	public void inorder(TreeNode root) { // 중위 순회로 탐색함
		if (root != null) {
			inorder(root.left);
			System.out.printf(" %c", root.data);
			inorder(root.right);
		}

	}

	public void printBST() {
		inorder(root);
		System.out.println(" 출력");

	}

}
{% endhighlight %}

BinarySearchTree_Test.java

{% highlight java %}
public class BinarySearchTree_Test {

	public static void main(String[] args) {

		BinarySearchTree bst = new BinarySearchTree();
		bst.insertBST('a');
		bst.insertBST('b');
		bst.insertBST('c');
		bst.insertBST('d');
		bst.insertBST('e');
		bst.insertBST('f');
		bst.insertBST('g');
		bst.insertBST('h');

		System.out.println("이진 탐색 트리");
		System.out.print("이진 트리 :");
		bst.printBST();

		System.out.print("탐색 -> ");
		TreeNode p1 = bst.searchBST('e');

		if (p1 != null) {
			System.out.println("탐색 성공 : " + p1.data);

		} else {
			System.out.println("탐색 실패 데이터가 존재하지 않음");

		}

	}

}
{% endhighlight %}




참고문헌



[itdexter][itdexter]님, [secmem][secmem]님, [marobiana][marobiana]님, 책 - '자바로 배우는 쉬운 자료구조'

[itdexter]: http://itdexter.tistory.com/82
[secmem]: http://secmem.tistory.com/204
[marobiana]: http://marobiana.tistory.com/83

update : 2016-03-07