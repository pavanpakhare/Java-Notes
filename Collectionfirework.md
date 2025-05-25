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
