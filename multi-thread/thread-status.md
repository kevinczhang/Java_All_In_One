# Synchronization

![Thread status](../.gitbook/assets/image%20%284%29.png)

1. **synchronized** keyword is used for exclusive accessing. 
2. To make a **method synchronized**, simply add the synchronized keyword to its declaration. Then no two invocations of synchronized methods on the same object can interleave with each other. 
3. Synchronized statements must specify the object that provides the intrinsic lock. When **synchronized\(this\)** is used, you have to avoid to synchronizing invocations of other objects' methods.
4. **wait\(\)** tells the calling thread to give up the monitor and go to sleep until some other thread enters the same monitor and calls **notify\( \)**. **notify\(\)** wakes up the first thread that called **wait\(\)** on the same object.

## Method synchronized

```java
/**
 * {@code synchronized} ("only let one thread in here at a time".) and 
 * {@code join} ("wait until * thread on which join has called finished") keyword.
 */
public class Worker {

    private int count = 0;

    public static void main(String[] args) {
        Worker worker = new Worker();
        worker.doWork();
    }

    /**
     * Run code again by removing the synchronized and join keywords By removing
     * synchronized keyword count variable will vary that is it is not atomic in
     * this case due to the reason that count is shared between the threads or
     * without join keyword count will output wrong.
     */
    public synchronized void increment(String threadName) throws InterruptedException {
        count++;
        //Thread.sleep(1000);
        System.out.println("Thread in Progress: " + threadName + " and count is: " + count);
    }

    public void doWork() {
        Thread thread1 = new Thread(new Runnable() {
            public void run() {
                for (int i = 0; i < 10; i++) {
                    try {
                        increment(Thread.currentThread().getName());
                    } catch (InterruptedException ex) {
                        Logger.getLogger(Worker.class.getName()).log(Level.SEVERE, null, ex);
                    }
                }
            }
        });
        thread1.start();
        Thread thread2 = new Thread(new Runnable() {
            public void run() {
                for (int i = 0; i < 10; i++) {
                    try {
                        increment(Thread.currentThread().getName());
                    } catch (InterruptedException ex) {
                        Logger.getLogger(Worker.class.getName()).log(Level.SEVERE, null, ex);
                    }
                }
            }
        });
        thread2.start();

        /**
         * Join Threads: Finish until thread finishes execution, then progress
         * the code Reminder: your method is also a thread so without joining
         * threads System.out.println("Count is: " + count); will work
         * immediately. Join does not terminate Thread 2, just progress of the
         * code stops until Threads terminate.
         */
        try {
            thread1.join();
            thread2.join();
        } catch (InterruptedException ignored) {}
        System.out.println("Count is: " + count);
    }
}
```

## Synchronized statements

```java
public class Worker {

    private Random random = new Random();

    private final Object lock1 = new Object();
    private final Object lock2 = new Object();

    private List<Integer> list1 = new ArrayList<>();
    private List<Integer> list2 = new ArrayList<>();

    public void stageOne() {

        synchronized (lock1) {
            try {
                Thread.sleep(1);
            } catch (InterruptedException e) {
                //do your work here
                e.printStackTrace();
            }
            list1.add(random.nextInt(100));
        }
    }

    public void stageTwo() {
        synchronized (lock2) {
            try {
                Thread.sleep(1);
            } catch (InterruptedException e) {
                //do your work here
                e.printStackTrace();
            }
            list2.add(random.nextInt(100));
        }

    }

    public void process() {
        for (int i = 0; i < 1000; i++) {
            stageOne();
            stageTwo();
        }
    }

    public void main() {
        System.out.println("Starting ...");
        long start = System.currentTimeMillis();
        Thread t1 = new Thread(new Runnable() {
            public void run() {
                process();
            }
        });

        Thread t2 = new Thread(new Runnable() {
            public void run() {
                process();
            }
        });

        t1.start();
        t2.start();

        try {
            t1.join();
            t2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        long end = System.currentTimeMillis();

        System.out.println("Time taken: " + (end - start));
        System.out.println("List1: " + list1.size() + "; List2: " + list2.size());
    }
}
```

```java
public class LockedATM {
	private Lock lock;
	private int balance = 100;
	
	public LockedATM(){
		lock = new ReentrantLock();
	}
	
	public int withdraw(int value){
		lock.lock();
		int temp = this.balance;
		try{
			Thread.sleep(100);
			temp -= value;
			Thread.sleep(100);
			this.balance = temp;
		} catch(InterruptedException e){
			e.printStackTrace();
		}
		lock.unlock();
		return temp;
	}

	public int depoit(int value){
		lock.lock();
		int temp = this.balance;
		try{
			Thread.sleep(100);
			temp += value;
			Thread.sleep(100);
			this.balance = temp;
		} catch(InterruptedException e){
			e.printStackTrace();
		}
		lock.unlock();
		return temp;
	}
}

```

