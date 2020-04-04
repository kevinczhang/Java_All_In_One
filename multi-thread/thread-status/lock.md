---
description: This is the base interface for Lock API.
---

# Lock

It provides all the features of synchronized keyword with additional ways to create different Conditions for locking, providing timeout for thread to wait for lock. Some of the important methods are lock\(\) to acquire the lock, unlock\(\) to release the lock, tryLock\(\) to wait for lock for a certain period of time, newCondition\(\) to create the Condition etc.

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

