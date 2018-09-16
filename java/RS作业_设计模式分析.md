

装饰者

```java
package java.util;
//具有同步性能的包装类
public static <T> Collection<T> synchronizedCollection(Collection<T> c){}
static class SynchronizedCollection<E> implements Collection<E>{}
//类型检查功能的包装类
public static <E> Collection<E> checkedCollection(Collection<E> c,Class<E> type){}
static class CheckedCollection<E> implements Collection<E>{}
//具有只读功能的包装类
public static <T> Collection<T> unmodifiableCollection(Collection<T> c){}
static class UnmodifiableCollection<E> implements Collection<E>{}
```





静态工厂方法

```java
//Executors中创建执行服务的静态工厂方法，对ThreadPoolExecutor()预定义
public static ExecutorService newFixedThreadPool(int nThreads){}
public static ExecutorService newSingleThreadExecutor(){}
public static ExecutorService newCachedThreadPool(){}
public static ExecutorService newWorkStealingPool(){}
//--------
//得到空迭代器的静态工厂方法
public static <T> Iterator<T> emptyIterator() {}
//得到空集合的静态工厂方法
public static final <T> Set<T> emptySet(){}
public static final <T> List<T> emptyList(){}
```



单例模式

```java
//EmptyIterator为私有类，外部无法访问到，避免了重复创建
private static class EmptyIterator<E> implements Iterator<E> {
        static final EmptyIterator<Object> EMPTY_ITERATOR = new EmptyIterator<>();
        public boolean hasNext() { return false; }
        public E next() { throw new NoSuchElementException(); }
        public void remove() { throw new IllegalStateException(); }
    }
//外部只能通过该方法获取单例的实例
public static <T> Iterator<T> emptyIterator() {return EmptyIterator.EMPTY_ITERATOR;}
```



迭代器

```java
//所有迭代子的父接口
public interface Iterator<E> {
    boolean hasNext();
    E next();
    void remove()；
}
//较早的枚举接口，设计理念是类似的
public interface Enumeration<E> {
    boolean hasMoreElements();
    E nextElement();
}
```



策略模式

```java
//Collections中提供的一些算法
public static <T> int binarySearch(List<T> list, T key, Comparator<T> c){}//二分查找
public static void reverse(List<?> list){}//逆序
public static void shuffle(List<?> list){}//洗牌
public static <T> void copy(List<T> dest, List<T> src){}//复制
//还有Arrays也针对Array提供了一些算法,主要是排序和查找
public static void sort(int[] a){}
private static void mergeSort(int[] a){}
public static void parallelSort(int[] a){}
```







