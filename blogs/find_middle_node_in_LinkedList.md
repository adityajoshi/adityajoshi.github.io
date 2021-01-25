# Find middle node in LinkedList

```
import java.util.Optional;

public class LinkedListMiddleNode {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		Node head = createList();
		Optional<String> middle = findMiddle(head);
		middle.ifPresent(System.out::println);
	}
	
	public static Optional<String> findMiddle(Node head){
		Node fastPointer = head;
		Node slowPointer = head;
		
		while(fastPointer.hasNext() && fastPointer.getNext().hasNext()) {
			fastPointer = fastPointer.getNext().getNext();
			slowPointer = slowPointer.getNext();
		}
		return Optional.ofNullable(slowPointer.getData());
	}

	public static Node createList() {
		Node head = new Node("1");
		Node current = head;
		
		for(int i=2;i<=10;i++) {
			Node newNode = new Node(String.valueOf(i));
			current.setNext(newNode);
			current = newNode;
		}
		return head;
	}
}

class Node {
	private String data;
	private Node next;

	public String getData() {
		return data;
	}

	public void setData(String data) {
		this.data = data;
	}

	public Node getNext() {
		return next;
	}

	public void setNext(Node next) {
		this.next = next;
	}

	public Node(String data) {
		super();
		this.data = data;
		this.next = null;
	}

	public boolean hasNext() {
		return next != null;
	}

}
```
