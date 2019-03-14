# Thread status

![Thread status](../.gitbook/assets/image%20%284%29.png)

1. synchronized keyword is used for exclusive accessing. 
2. To make a method synchronized, simply add the synchronized keyword to its declaration. Then no two invocations of synchronized methods on the same object can interleave with each other. 
3. Synchronized statements must specify the object that provides the intrinsic lock. When synchronized\(this\) is used, you have to avoid to synchronizing invocations of other objects' methods.
4. wait\(\) tells the calling thread to give up the monitor and go to sleep until some other thread enters the same monitor and calls notify\( \). notify\(\) wakes up the first thread that called wait\(\) on the same object.

