# Callable and Future

However, one feature lacking in Runnable is that we cannot make a thread return result when it terminates, i.e. when run\(\) completes. For supporting this feature, the Callable interface is present in Java.

**Callable vs Runnable**

* For implementing Runnable, the run\(\) method needs to be implemented which does not return anything, while for a Callable, the call\(\) method needs to be implemented which returns a result on completion. Note that a thread can’t be created with a Callable, it can only be created with a Runnable.
* Another difference is that the call\(\) method can throw an exception whereas run\(\) cannot.

### Callable

Java Callable interface use Generic to define the return type of Object. [Executors](https://www.journaldev.com/1069/threadpoolexecutor-java-thread-pool-example-executorservice) class provide useful methods to execute Java Callable in a thread pool. Since callable tasks run in parallel, we have to wait for the returned Object.

### Future

Future is basically one way the main thread can keep track of the progress and result from other threads. Java Callable tasks return **java.util.concurrent.Future** object. Using **Java Future** object, we can find out the status of the Callable task and get the returned Object. It provides **get\(\)** method that can wait for the Callable to finish and then return the result.

Java Future provides **cancel\(\)** method to cancel the associated Callable task. There is an overloaded version of get\(\) method where we can specify the time to wait for the result, it’s useful to avoid current thread getting blocked for longer time. There are **isDone\(\)** and **isCancelled\(\)** methods to find out the current status of associated Callable task.

```java
public class App {

    public static void main(String[] args) throws InterruptedException {
        ExecutorService executor = Executors.newCachedThreadPool();

        //anonymous call of Callable
        Future<Integer> future = executor.submit(new Callable<Integer>() {

            @Override
            //return value is Integer
            public Integer call() throws TimeoutException {
                Random random = new Random();
                int duration = random.nextInt(4000);
                if (duration > 2000) {
                    throw new TimeoutException ("Sleeping for too long.");
                }

                System.out.println("Starting ...");
                try {
                    Thread.sleep(duration);
                } catch (InterruptedException ignored) {}
                System.out.println("Finished.");
                return duration;
            }
        });

        executor.shutdown();
//        executor.awaitTermination(1, TimeUnit.DAYS);
        try {
            //get returned value from call()
            System.out.println("Result is: " + future.get());

        } catch (InterruptedException ignored) {
        } catch (ExecutionException e) {
            TimeoutException ex = (TimeoutException) e.getCause();
            System.out.println(ex.getMessage());
        }
    }

}
```

