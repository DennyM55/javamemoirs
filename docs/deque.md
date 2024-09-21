### Notes on Deque

A **Deque** (pronounced "deck") stands for **Double-Ended Queue**. It is a linear collection that supports the insertion and removal of elements from both ends: the front and the rear. This flexibility makes it more versatile than a regular queue, which only allows insertion at the rear and removal from the front.

#### Key Characteristics:
- **Double-Ended**: Elements can be added or removed from both ends.
- **Linear Collection**: Similar to a queue or stack, but with more versatility.
- **Generic**: It can hold any type of object.

#### Deque in Java
In Java, `Deque` is an interface in the `java.util` package and is implemented by classes such as `ArrayDeque`, `LinkedList`, etc.

```java
Deque<Integer> deque = new LinkedList<>();
```

### Operations Supported by Deque

1. **Adding Elements**:
   - **`offerFirst(E e)`**: Adds the specified element at the front (head) of the deque.
   - **`offerLast(E e)`**: Adds the specified element at the end (tail) of the deque.
   - **`addFirst(E e)`**: Inserts the specified element at the front. Throws an exception if it fails.
   - **`addLast(E e)`**: Inserts the specified element at the end. Throws an exception if it fails.
   - **`offer(E e)`**: Adds the element at the end of the deque (equivalent to `offerLast`).
   - **`add(E e)`**: Adds the element at the end (equivalent to `addLast`).

   **Example**:
   ```java
   Deque<Integer> deque = new ArrayDeque<>();
   deque.offerFirst(1);  // [1]
   deque.offerLast(2);   // [1, 2]
   deque.addFirst(3);    // [3, 1, 2]
   deque.addLast(4);     // [3, 1, 2, 4]
   ```

2. **Removing Elements**:
   - **`pollFirst()`**: Retrieves and removes the first element; returns `null` if the deque is empty.
   - **`pollLast()`**: Retrieves and removes the last element; returns `null` if the deque is empty.
   - **`removeFirst()`**: Removes the first element; throws an exception if the deque is empty.
   - **`removeLast()`**: Removes the last element; throws an exception if the deque is empty.
   - **`poll()`**: Retrieves and removes the head of the deque (equivalent to `pollFirst`).
   - **`remove()`**: Retrieves and removes the head of the deque (equivalent to `removeFirst`).

   **Example**:
   ```java
   Deque<Integer> deque = new ArrayDeque<>(Arrays.asList(1, 2, 3, 4));
   deque.pollFirst();  // Removes 1 -> [2, 3, 4]
   deque.pollLast();   // Removes 4 -> [2, 3]
   deque.remove();     // Removes 2 -> [3]
   ```

3. **Retrieving Elements**:
   - **`peekFirst()`**: Retrieves the first element without removing it; returns `null` if the deque is empty.
   - **`peekLast()`**: Retrieves the last element without removing it; returns `null` if the deque is empty.
   - **`getFirst()`**: Retrieves the first element; throws an exception if the deque is empty.
   - **`getLast()`**: Retrieves the last element; throws an exception if the deque is empty.
   - **`peek()`**: Retrieves the head of the deque (equivalent to `peekFirst`).
   - **`element()`**: Retrieves the head of the deque (equivalent to `getFirst`).

   **Example**:
   ```java
   Deque<Integer> deque = new ArrayDeque<>(Arrays.asList(1, 2, 3));
   System.out.println(deque.peekFirst()); // 1
   System.out.println(deque.peekLast());  // 3
   System.out.println(deque.element());   // 1
   ```

4. **Removing Specific Elements**:
   - **`removeFirstOccurrence(Object o)`**: Removes the first occurrence of the specified element.
   - **`removeLastOccurrence(Object o)`**: Removes the last occurrence of the specified element.

   **Example**:
   ```java
   Deque<String> deque = new ArrayDeque<>(Arrays.asList("a", "b", "a", "c"));
   deque.removeFirstOccurrence("a"); // Removes the first "a" -> ["b", "a", "c"]
   deque.removeLastOccurrence("a");  // Removes the last "a" -> ["b", "c"]
   ```

5. **Iteration**:
   - You can iterate through the deque using a standard iterator, or you can specifically iterate from the head or tail.
   - **`descendingIterator()`**: Returns an iterator that traverses the elements in reverse order.

   **Example**:
   ```java
   Deque<Integer> deque = new ArrayDeque<>(Arrays.asList(1, 2, 3, 4));
   for (Integer i : deque) {
       System.out.println(i);  // Prints 1, 2, 3, 4
   }
   Iterator<Integer> revIter = deque.descendingIterator();
   while (revIter.hasNext()) {
       System.out.println(revIter.next());  // Prints 4, 3, 2, 1
   }
   ```

### Common Implementations of Deque

1. **`ArrayDeque`**:
   - It is the most common implementation of `Deque`.
   - It is a resizable array that grows automatically when more space is needed.
   - No capacity restrictions.
   - Faster than `LinkedList` when used as a stack or queue.

   **Example**:
   ```java
   Deque<Integer> deque = new ArrayDeque<>();
   ```

2. **`LinkedList`**:
   - Implements both `Deque` and `List` interfaces.
   - Allows for constant-time insertions or removals from both ends.
   - Slower than `ArrayDeque` when used for queue operations.

   **Example**:
   ```java
   Deque<Integer> deque = new LinkedList<>();
   ```

### When to Use Deque?

- **Queue Operations**: When you need a double-ended queue to efficiently add or remove elements from both ends.
- **Stack Operations**: `Deque` can also be used as a stack (LIFO - Last In, First Out) by using methods like `push()`, `pop()`, and `peek()`.
- **Task Scheduling**: Ideal for task scheduling scenarios where tasks need to be processed from either end of the queue.
- **Undo/Redo Functionality**: Useful in applications that require undo/redo operations as you can access elements from both ends.

### Performance Considerations

- **ArrayDeque** is generally faster and preferred for most queue or stack operations.
- **LinkedList** is better suited when frequent insertions or deletions at both ends are required, especially when the total number of elements is not fixed.

### Deque as a Stack
A `Deque` can be used as a stack with methods such as:
- **`push(E e)`**: Pushes an element onto the stack represented by this deque.
- **`pop()`**: Pops an element from the stack represented by this deque.
- **`peek()`**: Retrieves, but does not remove, the head of the deque, which is the top of the stack.

**Example**:
```java
Deque<Integer> stack = new ArrayDeque<>();
stack.push(10); // [10]
stack.push(20); // [20, 10]
System.out.println(stack.pop()); // 20
System.out.println(stack.peek()); // 10
```

### Deque as a Queue
A `Deque` can be used as a queue with methods such as:
- **`offer(E e)`**: Inserts the specified element at the end of this deque.
- **`poll()`**: Retrieves and removes the head of the queue represented by this deque.
- **`peek()`**: Retrieves, but does not remove, the head of the queue.

**Example**:
```java
Deque<Integer> queue = new ArrayDeque<>();
queue.offer(10); // [10]
queue.offer(20); // [10, 20]
System.out.println(queue.poll()); // 10
System.out.println(queue.peek()); // 20
```

### Conclusion

The `Deque` interface is a versatile tool in Java that allows for both queue and stack-like operations. It provides a rich set of methods to manipulate elements from both ends efficiently. Understanding how to leverage `Deque` can help you write more efficient and cleaner code, especially in situations where you need more control over the order of processing elements.
