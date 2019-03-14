# Problems

## Calculate the expression 1\*2/\(1+2\)

Solution: Use one thread to do addition, one thread to do multiplication, and a main thread to do the division. Since there is no need to communicate data between threads, so only need to consider the order of thread execution. In the main thread, let addition and multiplication join the main thread. The join\(\) method is used when we want the parent thread waits until the threads which call join\(\) ends. In this case, we want addition and multiplication complete first and then do the division.

```java
class Add extends Thread {
	int value;
 
	public void run() {
		value = 1 + 2;
	}
}
 
class Mul extends Thread {
	int value;
 
	public void run() {
		value = 1 * 2;
	}
}
 
public class Main{
	public static void main(String[] args){
		Add t1 = new Add();
		Mul t2 = new Mul();
 
		t1.start();
		t2.start();
 
		try {
			t1.join();
			t2.join();
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
 
		double n = ((double)t2.value/t1.value);
 
		System.out.println(n);		
	}
}
```

## Producer and consumer

```java
// Sync Buffer to store products
public class Buffer {
	
	static final int CAPACITY = 3; // buffer size
	Queue<Integer> queue = new LinkedList<Integer>();
	// Create a new lock
	Lock lock = new ReentrantLock();

	// Create two conditions
	Condition notEmpty = lock.newCondition();
	Condition notFull = lock.newCondition();

	// Write to buffer
	public void write(int value) {
		lock.lock(); // Acquire the lock
		try {
			while (queue.size() == CAPACITY) {
				System.out.println("Wait for notFull condition");
				notFull.await();
			}
			queue.offer(value);
			System.out.println("Current queue size is " + queue.size());
			notEmpty.signal(); // Signal notEmpty condition
		} catch (InterruptedException ex) {
			ex.printStackTrace();
		} finally {
			lock.unlock(); // Release the lock
		}
	}

	// Read buffer
	public int read() {
		int value = 0;
		lock.lock(); // Acquire the lock
		try {
			while (queue.isEmpty()) {
				System.out.println("\t\t\tWait for notEmpty condition");
				notEmpty.await();
			}
			value = queue.remove();
			System.out.println("\t\t\tCurrent queue size is " + queue.size());
			notFull.signal(); // Signal notFull condition
		} catch (InterruptedException ex) {
			ex.printStackTrace();
		} finally {
			lock.unlock(); // Release the lock			
		}
		return value;
	}
}

// Producer's task
public class ProducerTask implements Runnable {
	@Override
	public void run() {
		try {
			int i = 1;
			while (true) {
				System.out.println("Producer writes " + i);
				ConsumerProducer.buffer.write(i++); // Add a value to the buffer
				// Put the thread to sleep
				Thread.sleep((int) (Math.random() * 10000));
			}
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
	}
}

// Consumer's task
public class ConsumerTask implements Runnable {
	@Override
	public void run() {
		try {
			while (true) {
				System.out.println("\t\t\tConsumer reads " + ConsumerProducer.buffer.read());
				// Put the thread to sleep
				Thread.sleep((int) (Math.random() * 10000));
			}
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
	}
}

// Bootstrap class with main method
public class ConsumerProducer {
	static Buffer buffer = new Buffer();
	public static void main(String[] args){
		// Create a thread pool with two threads
		ExecutorService executor =  Executors.newFixedThreadPool(2);
		executor.execute(new ProducerTask());
		executor.execute(new ConsumerTask());
		executor.shutdown();
	}
}
```

## Producer and consumer by blocking queue

From [http://javarevisited.blogspot.com/2012/02/producer-consumer-design-pattern-with.html](http://javarevisited.blogspot.com/2012/02/producer-consumer-design-pattern-with.html)

```java
public class ProducerConsumerPattern {
    public static void main(String args[]){
       //Creating shared object
       BlockingQueue sharedQueue = new LinkedBlockingQueue();
 
       //Creating Producer and Consumer Thread
       Thread prodThread = new Thread(new Producer(sharedQueue));
       Thread consThread = new Thread(new Consumer(sharedQueue));
       //Starting producer and Consumer thread
       prodThread.start();
       consThread.start();
    } 
}

//Producer Class in java
class Producer implements Runnable {
    private final BlockingQueue sharedQueue;
    public Producer(BlockingQueue sharedQueue) {
        this.sharedQueue = sharedQueue;
    }
    @Override
    public void run() {
        for(int i=0; i<10; i++){
            try {
                System.out.println("Produced: " + i);
                sharedQueue.put(i);
            } catch (InterruptedException ex) {
                Logger.getLogger(Producer.class.getName()).log(Level.SEVERE, null, ex);
            }
        }
    }
}

//Consumer Class in Java
class Consumer implements Runnable{
    private final BlockingQueue sharedQueue;
    public Consumer (BlockingQueue sharedQueue) {
        this.sharedQueue = sharedQueue;
    }
  
    @Override
    public void run() {
        while(true){
            try {
                System.out.println("Consumed: "+ sharedQueue.take());
            } catch (InterruptedException ex) {
                Logger.getLogger(Consumer.class.getName()).log(Level.SEVERE, null, ex);
            }
        }
    }  
}
```

