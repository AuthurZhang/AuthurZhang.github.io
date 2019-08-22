---
title: Java Review - Containers
date: 2019-06-20 16:07:37
tags:
- Java Containers
categories: 
- Java
top: 99
---
# Java Review - Containers

## Abstract
In this chapter, I would like to introduce the  collection of Java and then list several interview questions.

<!--more-->

## Containers taonomy
![](/images/java_containers_01.jpg)

## List
### The Difference between LinkedList and ArrayList?
1. Principle: 
- LinkedList is based on List, however ArrayList is based on array.
- Thus, LinkedList is good at inserting and deleting and ArrayList is good at searching.
2. Realization: 
- LinkedList extends AbstractSequentialList.
- And then the same as ArrayList, extends AbstractList.
- AbstractList extends AbstractCollection, implements List
- AbstractCollection implements Collection
- List extends Collection
- Collection extends Iterable( has iterator)

### The principle of realization of ArrayList?

ArrayList is dynamic array. We can know it is actually an array as follows
```bash
	/**
     * The array buffer into which the elements of the ArrayList are stored.
     * The capacity of the ArrayList is the length of this array buffer. Any
     * empty ArrayList with elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA
     * will be expanded to DEFAULT_CAPACITY when the first element is added.
     */
    transient Object[] elementData; // non-private to simplify nested class access

```

- Thus, when we new a arraylist object, it has a 10 empty capacity to store somethings. 
- When there is no enough space (for example the size is 10), add one more capacity.

```java
    public boolean add(E e) {
        ensureCapacityInternal(size + 1);  // Increments modCount!!
        elementData[size++] = e;
        return true;
    }
    
    private void ensureCapacityInternal(int minCapacity) {
        ensureExplicitCapacity(calculateCapacity(elementData, minCapacity));
    }

    private void ensureExplicitCapacity(int minCapacity) {
        modCount++;

        // overflow-conscious code
        if (minCapacity - elementData.length > 0)
            grow(minCapacity);
    }
```

As we can see, every time use add function, we need to do ensureCapacityInternal, and then grow the length.
```java
    private void grow(int minCapacity) {
        // overflow-conscious code
        int oldCapacity = elementData.length;
        int newCapacity = oldCapacity + (oldCapacity >> 1);
        if (newCapacity - minCapacity < 0)
            newCapacity = minCapacity;
        if (newCapacity - MAX_ARRAY_SIZE > 0)
            newCapacity = hugeCapacity(minCapacity);
        // minCapacity is usually close to size, so this is a win:
        elementData = Arrays.copyOf(elementData, newCapacity);
    }
```
Every time the function grow executes, we clone a new array, thus it is bad to do inserting.



### ArrayList, LinkedList and Vector, which one is thread safety? why?

Vector is thread safety.
```java
    public synchronized boolean add(E e) {
        modCount++;
        ensureCapacityHelper(elementCount + 1);
        elementData[elementCount++] = e;
        return true;
    }
```
Almost every function in Vector use word synchronized, thus it is synchronized.
And Stack extends Vector, thus Stack is also safe.



### What about Queue? 

There several kinds of queue.

There are two non-blocking queue: PriorityQueue and ConcurrentLinkedQueue.

- PriorityQueue extends AbstractQueue

- AbstractQueue extends AbstractCollection

- ConcurrentLinkedQueue almost the same.

There are some blocking queue: 

- ArrayBlockingQueue

- LinkedBlockingQueue

- PriorityBlockingQueue

- ...

### what is the difference between blocking queue and non-blocking queue?

Blocking queue works like when the queue is full, we cannot do put operation.

## HaspMap
### The Realization of HashMap?

The core of "Hash" is Hash Table, and Hash Table is realized by "拉链法" in HashMap.

It has two important attributes: table(Entry[]) and threshold.

- table: table is realized by class Entry(implements Map)
```java
    static class Node<K,V> implements Map.Entry<K,V> {
        final int hash;
        final K key;
        V value;
        Node<K,V> next;

        Node(int hash, K key, V value, Node<K,V> next) {
            this.hash = hash;
            this.key = key;
            this.value = value;
            this.next = next;
        }
    }
```
Actually, Entry is like a List.
- threshold: decide whether to add the capacity of map.
```java
    /**
     * The next size value at which to resize (capacity * load factor).
     *
     * @serial
     */
    // (The javadoc description is true upon serialization.
    // Additionally, if the table array has not been allocated, this
    // field holds the initial array capacity, or zero signifying
    // DEFAULT_INITIAL_CAPACITY.)
    int threshold;
```

### How to realize put and get function of HashMap?

```java
    public V put(K key, V value) {
        return putVal(hash(key), key, value, false, true);
    }
```

put() realizes the function putVal()

- if have the same hash value, put into the List. 

```java
    final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
                   boolean evict) {
        Node<K,V>[] tab; Node<K,V> p; int n, i;
        if ((tab = table) == null || (n = tab.length) == 0)
            n = (tab = resize()).length;
        if ((p = tab[i = (n - 1) & hash]) == null)
            tab[i] = newNode(hash, key, value, null);
        else {
            Node<K,V> e; K k;
            if (p.hash == hash &&
                ((k = p.key) == key || (key != null && key.equals(k))))
                e = p;
            else if (p instanceof TreeNode)
                e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
            else {
                for (int binCount = 0; ; ++binCount) {
                    if ((e = p.next) == null) {
                        p.next = newNode(hash, key, value, null);
                        if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                            treeifyBin(tab, hash);
                        break;
                    }
                    if (e.hash == hash &&
                        ((k = e.key) == key || (key != null && key.equals(k))))
                        break;
                    p = e;
                }
            }
            if (e != null) { // existing mapping for key
                V oldValue = e.value;
                if (!onlyIfAbsent || oldValue == null)
                    e.value = value;
                afterNodeAccess(e);
                return oldValue;
            }
        }
        ++modCount;
        if (++size > threshold)
            resize();
        afterNodeInsertion(evict);
        return null;
    }
```

### How to get hash num?

```java
static final int hash(Object key) {
    int h;
    return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
}
```

### How to find: function get()

Thus, first find in by table index, and then find in the list use key.

**HashMap use the hashCode() of Key to get the value**

```java
public V get(Object key) {
    Node<K,V> e;
    return (e = getNode(hash(key), key)) == null ? null : e.value;
}
```

```java
final Node<K,V> getNode(int hash, Object key) {
    Node<K,V>[] tab; Node<K,V> first, e; int n; K k;
    if ((tab = table) != null && (n = tab.length) > 0 &&
        (first = tab[(n - 1) & hash]) != null) {
        if (first.hash == hash && // always check first node
            ((k = first.key) == key || (key != null && key.equals(k))))
            return first;
        if ((e = first.next) != null) {
            if (first instanceof TreeNode)
                return ((TreeNode<K,V>)first).getTreeNode(hash, key);
            do {
                if (e.hash == hash &&
                    ((k = e.key) == key || (key != null && key.equals(k))))
                    return e;
            } while ((e = e.next) != null);
        }
    }
    return null;
}
```

### Function hashCode()

Simply put, **hashCode**() returns an integer value, generated by a hashing algorithm. Objects that are equal (according to their equals()) must return the same **hash code**.**It’s not required for different objects to return different hash codes.**

General hashCode() statement?

- same object - return same value
- two objects are equal according to the *equals(Object)* method - must the same value of hashCode
- has the same hashcode() return value - may not be the same object

### hashCode() and equals()

hashcode() is useful to do a quick search. 

**euqals() means really equal but hashcode() is not equal** 

For example, when we add an element in Set, we need to confirm whether there is the same element in the set, first we use hashcode(), is the same then use equal, if not just abort.

### Handling Hash Collisions

- **open addressing(linear probing)** - find the next open address
- **rehashing** - do hash again
- **chaining** - **When two or more objects point to the same bucket, they’re simply stored in a linked list.** Actually, the data structure of Entry realizes this function.

### Why override hashcode() when overriding equals()?

see two examples in **Integer** and **String**:

In Integer:

```java
public static int hashCode(int value) {
    return value;
}
```

```java
public boolean equals(Object obj) {
    if (obj instanceof Integer) {
        return value == ((Integer)obj).intValue();
    }
    return false;
}
```

In String:

```java
public int hashCode() {
    int h = hash;
    if (h == 0 && value.length > 0) {
        char val[] = value;

        for (int i = 0; i < value.length; i++) {
            h = 31 * h + val[i];
        }
        hash = h;
    }
    return h;
}
```

```java
public boolean equals(Object anObject) {
    if (this == anObject) {
        return true;
    }
    if (anObject instanceof String) {
        String anotherString = (String)anObject;
        int n = value.length;
        if (n == anotherString.value.length) {
            char v1[] = value;
            char v2[] = anotherString.value;
            int i = 0;
            while (n-- != 0) {
                if (v1[i] != v2[i])
                    return false;
                i++;
            }
            return true;
        }
    }
    return false;
}
```

### Differences between "==" and euqals() in Java?

- `==` -> is a reference comparison, i.e. both objects point to the same memory location
- `.equals()` -> evaluates to the comparison of values in the objects

