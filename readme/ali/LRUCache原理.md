# LRUCache原理

## 参考地址
    https://www.jianshu.com/p/b49a111147ee

## LRUCache简介
    LRUCache是一个对有限量的值持有强引用的缓存。其中的值每次被访问以后都会被移到队列头部。当一个值被添加到
    一个满载的缓存时，在队尾的值就会被移除队列，进而被垃圾回收器回收。
    
    LruCache这个类在android.util包下，是API level 12引入的，对于API level 12之前的系统可以使用support library
    中的LruCache。这个类非常适合用来缓存图片。
    
    主要算法原理：
        是把最近使用的对象用强引用存储在 LinkedHashMap 中，并且把最近最少使用的对象在缓存值达到预设定值之后从内存中移除。
        
        LruCache中维护了一个集合LinkedHashMap，该LinkedHashMap是以访问顺序排序的。当调用put()方法时，就会在结合中添加元素，
        并调用trimToSize()判断缓存是否已满，如果满了就用LinkedHashMap的迭代器删除队尾元素，即近期最少访问的元素。
        当调用get()方法访问缓存对象时，就会调用LinkedHashMap的get()方法获得对应集合元素，同时会更新该元素到队头。
        

