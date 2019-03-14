# Thread creation

## Extending Thread vs Implement Runnable

Implementing Runnable interface is preferable because:

* Java does not support multiple inheritance. Therefore extending the Thread class means that the sub class cannot extends any other class. A class implementing the Runnable interface will be able to extend another class.
* A class might only be interested in being runnable, and therefore, inheriting the full overhead of the Thread class would be excessive.

## By extending Thread class

```java
class Runner extends Thread{
	@Override
	public void run() {
		for(int i=0; i<10; i++){
			System.out.println("Hello " + i);
			try {
				Thread.sleep(100);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
	}	
}
```

## By implementing Runnable interface

```java
class Runner implements Runnable{
	@Override
	public void run() {
		for(int i=0; i<11; i++){
			System.out.println("Hello " + i);
			try {
				Thread.sleep(100);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}		
	}	
}
```

## Use Thread with Runnable interface

```java
public class App {
	public static void main(String[] args) {
		Thread t1 = new Thread(new Runnable(){
			@Override
			public void run() {
				for(int i=0; i<11; i++){
					System.out.println("Hello " + i);
					try {
						Thread.sleep(100);
					} catch (InterruptedException e) {
						e.printStackTrace();
					}
				}
			}
			
		});
		t1.start();
	}
}
```

