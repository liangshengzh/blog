title: 单链表反转
date: 2016-05-05 23:14:26
categories: 算法
tags:
- 算法
---

给你一个单链表，如何进行反转呢？比如A－>B->C->D反转过来是D->C->B->A

首先我们来定义一个单链表节点的数据结构，其中data用来保存节点的数据，next指向下一个节点。

```java
public class Node<T> {
    private T data;
    private Node next;


    public Node(T data) {
        this.data = data;
    }

    public Node(T data, Node next) {
        this.data = data;
        this.next = next;
    }

    public T getData() {
        return data;
    }

    public void setData(T data) {
        this.data = data;
    }

    public Node getNext() {
        return next;
    }

    public void setNext(Node next) {
        this.next = next;
    }
}
```

链表有以下几种方法：

##### 方法1
最简单粗暴的方法，直接把链表遍历一边，转换成一个数组，然后逆序遍历数组再转换成一个链表.
```java
public class ReverseSingleList2 {


    public static Node reserve(Node node){
        if(node == null || node.getNext() ==null){
            return node;
        }
        List<Node> nodeList = new ArrayList<>();
        while (node != null){
            nodeList.add(node);
            node = node.getNext();
        }
        Node[] nodes = nodeList.toArray(new Node[]{});
        for(int i = nodes.length - 1; i>0; i--){
            nodes[i].setNext(nodes[i-1]);
        }
        nodes[0].setNext(null);
        return nodes[nodes.length - 1];
    }


    public static void main(String[] args){
        Node<String> nodeA= new Node<String>("A");
        Node<String> nodeB= new Node<String>("B");
        Node<String> nodeC= new Node<String>("C");
        Node<String> nodeD= new Node<String>("D");
        nodeA.setNext(nodeB);
        nodeB.setNext(nodeC);
        nodeC.setNext(nodeD);

        printNode(reserve(nodeA));
    }

    private static  void printNode(Node node){
        while (node != null){
            System.out.print(node.getData() +"-->");
            node = node.getNext();
        }
        System.out.println();
    }
}
```
##### 方法2
遍历链表，逐个节点进行反转。pre和curr分别保存当前节点和前一个节点，把前一个节点设置当前节点的下一个节点，通过curr的不断后移，逐个反转节点。
pre  -->null
curr -->A->B->C->D

pre  -->A
curr -->B->C->D

pre  -->B->A
curr -->C->D

pre  -->C->B->A
curr -->D

pre  -->D->C->B->A
curr -->null
```java
public class ReverseSingleList1 {

    public static Node reserve(Node node){
        Node currentNode = node;
        Node previousNode = null;
        Node nextNode = null;
        while (currentNode != null){
            nextNode = currentNode.getNext();
            currentNode.setNext(previousNode);
            previousNode = currentNode;
            currentNode = nextNode;
        }

        return previousNode;
    }

    public static void main(String[] args){
        Node<String> nodeA= new Node<String>("A");
        Node<String> nodeB= new Node<String>("B");
        Node<String> nodeC= new Node<String>("C");
        Node<String> nodeD= new Node<String>("D");
        nodeA.setNext(nodeB);
        nodeB.setNext(nodeC);
        nodeC.setNext(nodeD);

        printNode(reserve(nodeA));
    }

    private static  void printNode(Node node){
        while (node != null){
            System.out.print(node.getData() +"-->");
            node = node.getNext();
        }
    }
}
```

##### 方法3:
通过递归的特点，把前一个节点的next设置为当前节点实现反转。

```java
public class ReverseSingleList {

    public static Node reserve(Node node){
        if (node ==  null || node.getNext() == null ){
            return node;
        }
        Node reserveHead = reserve(node.getNext());
        node.getNext().setNext(node);
        node.setNext(null);
        return reserveHead;
    }

    public static void main(String[] args){
        Node<String> nodeA= new Node<String>("A");
        Node<String> nodeB= new Node<String>("B");
        Node<String> nodeC= new Node<String>("C");
        Node<String> nodeD= new Node<String>("D");
        nodeA.setNext(nodeB);
        nodeB.setNext(nodeC);
        nodeC.setNext(nodeD);

        printNode(reserve(nodeA));
    }

    private static  void printNode(Node node){
        while (node != null){
            System.out.print(node.getData() +"-->");
            node = node.getNext();
        }
    }
}
```
