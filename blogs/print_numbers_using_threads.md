# Print Number with 2 threads and convert same to ExecutorService.

* Use a variable called odd of type boolean. If you want to print odd number, it’s value should be true and false for even.
* Create two methods printOdd() and printEven(), one will print odd numbers and other will print even numbers.
* Create two threads, t2 for odd and t1 for even.
* t1 will call printEven() method and t2 will call printOdd() method simultaneously.
* If boolean odd is true in printEven() method, t1 will wait.
* If boolean odd is false in printOdd() method, t2 will wait.

## Code:
```java
class PrintTask {
	boolean odd;
	int num = 1;
	int max = 20;

	public void printOdd() {
		synchronized (this) {
			while (num < max) {
				while (!odd) {
					try {
						wait();
					} catch (InterruptedException e) {
						// TODO Auto-generated catch block
						e.printStackTrace();
					}
				}
				odd = false;
				System.out.println("Odd thread :: " + num);
				num++;
				notify();
			}
		}
	}

	public void printEven() {
		synchronized (this) {
			while (num < max) {
				while (odd) {
					try {
						wait();
					} catch (InterruptedException e) {
						// TODO Auto-generated catch block
						e.printStackTrace();
					}
				}
				System.out.println("Even thread :: " + num);
				num++;
				odd = true;
				notify();
			}
		}
	}
}

public class PracticeClass {
	public static void main(String[] args) {
		PrintTask p = new PrintTask();
		p.odd = true;
//		Thread t1 = new Thread(()->{p.printOdd();});
//		Thread t2 = new Thread(()->{p.printEven();});
//		
//		t1.start();
//		t2.start();

		ExecutorService e = Executors.newFixedThreadPool(2);
		e.execute(() -> {
			p.printOdd();
		});
		e.execute(() -> {
			p.printEven();
		});

		e.shutdown();
	}

}
```
