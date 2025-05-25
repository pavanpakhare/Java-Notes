code 
```java
// Java Collections Cheat Sheet with Code Snippets

import java.util.*;

public class CheatSheet { public static void main(String[] args) { // List add List<Integer> list = new ArrayList<>(); list.add(10);

// Deque addFirst / addLast
    Deque<Integer> deque = new ArrayDeque<>();
    deque.addFirst(1);
    deque.addLast(2);

    // Queue offer / poll / peek
    Queue<Integer> queue = new LinkedList<>();
    queue.offer(3);
    int head = queue.peek();
    queue.poll();

    // Contains
    boolean hasElement = list.contains(10);

    // List get
    int val = list.get(0);

    // Map put / get / keySet / entrySet / remove
    Map<String, Integer> map = new HashMap<>();
    map.put("a", 1);
    int value = map.get("a");
    Set<String> keys = map.keySet();
    Set<Map.Entry<String, Integer>> entries = map.entrySet();
    map.remove("a");

    // Size / isEmpty / clear
    int size = list.size();
    boolean empty = list.isEmpty();
    list.clear();

    // Sort / reverse / max / min
    Collections.sort(list);
    Collections.reverse(list);
    int maximum = Collections.max(list);
    int minimum = Collections.min(list);

    // Binary search (sorted list)
    Collections.sort(list);
    int index = Collections.binarySearch(list, 10);

    // Fill / frequency
    Collections.fill(list, 5);
    int freq = Collections.frequency(list, 5);

    // Copy
    List<Integer> copyFrom = Arrays.asList(1, 2, 3);
    List<Integer> copyTo = new ArrayList<>(Arrays.asList(0, 0, 0));
    Collections.copy(copyTo, copyFrom);

    // Stream filter/map/reduce
    List<Integer> streamList = Arrays.asList(1, 2, 3, 4, 5);
    List<Integer> evens = streamList.stream().filter(x -> x % 2 == 0).toList();
    List<Integer> squared = streamList.stream().map(x -> x * x).toList();
    int sum = streamList.stream().reduce(0, Integer::sum

```


# Java Collections – Functions with Time and Space Complexity

A quick reference for competitive programming using Java Collections Framework.

| Function / Method                       | Type             | Use / Description                                                  | Time Complexity             | Space Complexity |
|----------------------------------------|------------------|--------------------------------------------------------------------|------------------------------|------------------|
| `add(E e)`                             | List, Set, Queue | Adds an element                                                    | O(1) avg (`ArrayList`), O(log n) in `TreeSet` | O(1)             |
| `addFirst(E e)` / `addLast(E e)`       | Deque            | Adds to front or back                                              | O(1)                         | O(1)             |
| `offer(E e)` / `offerFirst/Last()`     | Queue, Deque     | Adds element with return status                                    | O(1)                         | O(1)             |
| `remove()`                             | List, Queue      | Removes first element                                              | O(1) in `Queue`, O(n) in `ArrayList` | O(1)             |
| `poll()`                               | Queue, Deque     | Removes and returns head                                           | O(1)                         | O(1)             |
| `peek()`                               | Queue, Deque     | Returns head without removing                                      | O(1)                         | O(1)             |
| `contains(Object o)`                   | List, Set, Map   | Checks if element/key exists                                       | O(n) in `List`, O(1) in `HashSet/Map`, O(log n) in `TreeSet/Map` | O(1)             |
| `get(int index)`                       | List             | Access element by index                                            | O(1) in `ArrayList`, O(n) in `LinkedList` | O(1)             |
| `put(K key, V value)`                  | Map              | Inserts key-value                                                  | O(1) avg in `HashMap`, O(log n) in `TreeMap` | O(1)             |
| `get(K key)`                           | Map              | Retrieve value for a key                                           | O(1) in `HashMap`, O(log n) in `TreeMap` | O(1)             |
| `keySet()`                             | Map              | Returns set of all keys                                            | O(n)                         | O(n)             |
| `values()`                             | Map              | Returns collection of values                                       | O(n)                         | O(n)             |
| `entrySet()`                           | Map              | Returns key-value pairs                                            | O(n)                         | O(n)             |
| `remove(Object key)`                   | Map, Set         | Remove element/key                                                 | O(1) in `HashMap`, O(log n) in `TreeMap` | O(1)             |
| `size()`                               | Collection       | Number of elements                                                 | O(1)                         | O(1)             |
| `isEmpty()`                            | Collection       | Check if collection is empty                                       | O(1)                         | O(1)             |
| `clear()`                              | Collection       | Removes all elements                                               | O(n)                         | O(1)             |
| `sort(List)`                           | Collections      | Sorts list in natural order                                        | O(n log n)                   | O(log n) aux     |
| `reverse(List)`                        | Collections      | Reverses list                                                      | O(n)                         | O(1)             |
| `max(Collection)` / `min(Collection)` | Collections      | Finds max/min                                                      | O(n)                         | O(1)             |
| `binarySearch(List, T)`                | Collections      | Binary search (sorted list required)                               | O(log n)                     | O(1)             |
| `fill(List, T)`                        | Collections      | Fills list with a value                                            | O(n)                         | O(1)             |
| `frequency(Collection, T)`             | Collections      | Counts frequency of an element                                     | O(n)                         | O(1)             |
| `copy(dest, src)`                      | Collections      | Copies elements (size must match)                                  | O(n)                         | O(1)             |
| `stream()`                             | Collection       | Creates a stream                                                   | O(1)                         | O(1)             |
| `collect(Collectors.toList())`         | Stream           | Collects stream into a list                                        | O(n)                         | O(n)             |
| `filter(Predicate)`                    | Stream           | Filters stream elements                                            | O(n)                         | O(n)             |
| `map(Function)`                        | Stream           | Transforms stream elements                                         | O(n)                         | O(n)             |
| `reduce(identity, BinaryOperator)`     | Stream           | Aggregates stream values (sum, product, etc.)                      | O(n)                         | O(1)             |

---

### Tips

- Use `HashMap`/`HashSet` for fast lookups – O(1) average case.
- Prefer `ArrayDeque` over `Stack` and `LinkedList` for deque-based logic.
- Use `TreeMap` or `TreeSet` for sorted structures (O(log n) operations).
- Avoid using `LinkedList` for random access.
