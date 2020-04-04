---
description: This is the base interface for Lock API.
---

# ReentrantLock

1. **Lock**: This is the base interface for Lock API. It provides all the features of synchronized keyword with additional ways to create different Conditions for locking, providing timeout for thread to wait for lock. Some of the important methods are lock\(\) to acquire the lock, unlock\(\) to release the lock, tryLock\(\) to wait for lock for a certain period of time, newCondition\(\) to create the Condition etc.
2. **Condition**: Condition objects are similar to [Object wait-notify](https://www.journaldev.com/1037/java-thread-wait-notify-and-notifyall-example) model with additional feature to create different sets of wait. A Condition object is always created by Lock object. Some of the important methods are await\(\) that is similar to wait\(\) and signal\(\), signalAll\(\) that is similar to notify\(\) and notifyAll\(\) methods.
3. **ReadWriteLock**: It contains a pair of associated locks, one for read-only operations and another one for writing. The read lock may be held simultaneously by multiple reader threads as long as there are no writer threads. The write lock is exclusive.
4. **ReentrantLock**: This is the most widely used implementation class of Lock interface. This class implements the Lock interface in similar way as synchronized keyword. Apart from Lock interface implementation, ReentrantLock contains some utility methods to get the thread holding the lock, threads waiting to acquire the lock etc.

{% hint style="info" %}
synchronized block are reentrant in nature i.e if a thread has lock on the monitor object and if another synchronized block requires to have the lock on the same monitor object then thread can enter that code block. I think this is the reason for the class name to be ReentrantLock.
{% endhint %}

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

