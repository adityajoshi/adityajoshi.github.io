#Java - Find middle element in LinkedList

Given a singly linked list, find the middle of the linked list. For example, if the given linked list is 1->2->3->4->5 then the output should be 3. 
If there are even nodes, then there would be two middle nodes, we need to print the second middle element. For example, if given linked list is 1->2->3->4->5->6 then output should be 4. 

There are 2 approaches to solve this.

1. Traverse the whole linked list and count the no. of elements. Traverse the list again till count/2 and return the node at count/2. 

2. Traverse linked list using two pointers (Fast and Slow pointers). 
   Move one pointer by one and the other pointers by two. When the fast pointer reaches the end slow pointer will reach the middle of the linked list.
   
2nd Approach is more efficient as in 1st approach you are going to traverse list twice. This may not be a problem for list with 10 elements but can cause when size increases.


```
import java.util.Optional;

public class LinkedListMiddleElement {

	public static void main(String[] args) {
		Element head = createList();
		Optional<String> middle = findMiddle(head);
		middle.ifPresent(System.out::println);
	}
	
	public static Optional<String> findMiddle(Element head){
		Element fastPointer = head;
		Element slowPointer = head;
		
		while(fastPointer.hasNext() && fastPointer.getNext().hasNext()) {
			fastPointer = fastPointer.getNext().getNext();
			slowPointer = slowPointer.getNext();
		}
		return Optional.ofNullable(slowPointer.getData());
	}

	// Creating list of 10 elements
	public static Element createList() {
		Element head = new Element("1");
		Element current = head;
		
		for(int i=2;i<=10;i++) {
			Element newNode = new Element(String.valueOf(i));
			current.setNext(newNode);
			current = newNode;
		}
		return head;
	}
}

class Element {
	private String data;
	private Element next;

	public String getData() {
		return data;
	}

	public void setData(String data) {
		this.data = data;
	}

	public Element getNext() {
		return next;
	}

	public void setNext(Element next) {
		this.next = next;
	}

	public Element(String data) {
		super();
		this.data = data;
		this.next = null;
	}

	public boolean hasNext() {
		return next != null;
	}

}
```
