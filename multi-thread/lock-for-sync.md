# Lock for sync

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

