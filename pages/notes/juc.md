### JUC

#### concurrentModificationException 并发修改异常
     并发修改异常描述：当多个线程并发修改同一个集合时，会抛出并发修改异常。
     解决方案：使用CopyOnWriteArrayList集合，该集合在修改时，会复制一份新的集合，修改新的集合，不会影响原来的集合。
     CopyOnWriteArrayList集合的缺点：在修改时，会复制一份新的集合，会占用内存空间，效率较低。
     思想 COW（Copy On Write）写时复制

     解决方案：使用Collections.synchronizedList(list)方法，将集合转换为线程安全的集合。
     Collections.synchronizedList(list)方法：将集合转换为线程安全的集合，使用synchronized关键字进行同步。
     Collections.synchronizedList(list)方法的缺点：在修改时，会使用synchronized关键字进行同步，效率较低。

     解决方案：Vector集合，该集合是线程安全的集合，使用synchronized关键字进行同步。

#### 线程安全集合

#### volatile关键字