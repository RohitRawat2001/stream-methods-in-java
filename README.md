# stream-methods-in-java

# stream
In Java, streams provide a way to process sequences of elements, such as collections, arrays, or input sources, in a functional style. Streams support operations like filtering, mapping, and reducing, allowing for more expressive and efficient code. Below are some common stream methods in Java:

# 1. filter()
Description: Filters the elements of a stream based on a given predicate (a boolean condition).
Example:
```java
List<String> names = Arrays.asList("John", "Jane", "Jack");
List<String> filteredNames = names.stream()
                                  .filter(name -> name.startsWith("J"))
                                  .collect(Collectors.toList());
// Result: ["John", "Jane", "Jack"]
```

# 2. map()
Description: Transforms each element of the stream by applying a function to it. The resulting stream contains the transformed elements.

Example:
```java
List<Integer> numbers = Arrays.asList(1, 2, 3);
List<Integer> squares = numbers.stream()
                               .map(n -> n * n)
                               .collect(Collectors.toList());
// Result: [1, 4, 9]
```

# 3. flatMap()
Description: Similar to map(), but the function applied to each element produces a stream of values, and flatMap() flattens these streams into a single stream.
Example:
```java
List<List<String>> names = Arrays.asList(
    Arrays.asList("John", "Jane"),
    Arrays.asList("Jack", "Jill")
);
List<String> allNames = names.stream()
                             .flatMap(Collection::stream)
                             .collect(Collectors.toList());
// Result: ["John", "Jane", "Jack", "Jill"]
```

# 4. forEach()
Description: Performs an action for each element of the stream. This is a terminal operation, meaning it ends the stream.
Example:
```java
List<String> names = Arrays.asList("John", "Jane", "Jack");
names.stream().forEach(System.out::println);
// Output: John Jane Jack (each on a new line)
```

# 5. collect()
Description: Collects the elements of the stream into a collection or other data structure. This is a terminal operation.
Example:
```java
List<String> names = Arrays.asList("John", "Jane", "Jack");
Set<String> nameSet = names.stream()
                           .collect(Collectors.toSet());
// Result: Set containing "John", "Jane", "Jack"
```

# 6. reduce()
Description: Reduces the elements of the stream to a single value by repeatedly applying a binary operator.
Example:

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4);
int sum = numbers.stream()
                 .reduce(0, (a, b) -> a + b);
// Result: 10
```

# 7. sorted()
Description: Sorts the elements of the stream either in natural order or by a custom comparator.
Example:
```java
List<String> names = Arrays.asList("John", "Jane", "Jack");
List<String> sortedNames = names.stream()
                                .sorted()
                                .collect(Collectors.toList());
// Result: ["Jack", "Jane", "John"]
```

# 8. distinct()
Description: Returns a stream with duplicate elements removed.
Example:
```java
List<Integer> numbers = Arrays.asList(1, 2, 2, 3, 4, 4, 4);
List<Integer> distinctNumbers = numbers.stream()
                                       .distinct()
                                       .collect(Collectors.toList());
// Result: [1, 2, 3, 4]
```

# 9. limit()
Description: Limits the number of elements in the stream to the specified number.
Example:

```java
List<String> names = Arrays.asList("John", "Jane", "Jack", "Jill");
List<String> limitedNames = names.stream()
                                 .limit(2)
                                 .collect(Collectors.toList());
// Result: ["John", "Jane"]
```

# 10. skip()

- **Description:** Skips the first n elements of the stream.
- **Example:**
- 
```java
  List<String> names = Arrays.asList("John", "Jane", "Jack", "Jill");
  List<String> skippedNames = names.stream()
                                   .skip(2)
                                   .collect(Collectors.toList());
  // Result: ["Jack", "Jill"]
```
# 11. peek()

- **Description:** Allows you to perform an action on each element of the stream as it is processed, without consuming the stream.
- **Example:**
  ```java
  List<String> names = Arrays.asList("John", "Jane", "Jack");
  names.stream()
       .peek(System.out::println)
       .collect(Collectors.toList());
  // Output: John Jane Jack (each on a new line)
  ```
# 12. allMatch(), anyMatch(), noneMatch()

- **Description:** These methods check if all, any, or none of the elements in the stream match a given predicate.
- **Example:**
  ```java
  List<Integer> numbers = Arrays.asList(2, 4, 6);
  boolean allEven = numbers.stream().allMatch(n -> n % 2 == 0);
  // Result: true

  boolean anyEven = numbers.stream().anyMatch(n -> n % 2 == 0);
  // Result: true

  boolean noneOdd = numbers.stream().noneMatch(n -> n % 2 != 0);
  // Result: true
  ```
# 13. findFirst() and findAny()

- **Description:** Returns the first or any element from the stream, respectively. Both return an `Optional`.
- **Example:**
  ```java
  List<String> names = Arrays.asList("John", "Jane", "Jack");
  Optional<String> firstName = names.stream().findFirst();
  // Result: Optional containing "John"

  Optional<String> anyName = names.stream().findAny();
  // Result: Optional containing any name, usually "John"
  ```
# 14. count()

- **Description:** Counts the number of elements in the stream. This is a terminal operation.
- **Example:**
  ```java
  List<String> names = Arrays.asList("John", "Jane", "Jack");
  long count = names.stream().count();
  // Result: 3
  ```
# 15. max() and min()

- **Description:** Returns the maximum or minimum element of the stream according to a given comparator. Both return an `Optional`.
- **Example:**
  ```java
  List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
  Optional<Integer> max = numbers.stream().max(Integer::compareTo);
  Optional<Integer> min = numbers.stream().min(Integer::compareTo);
  // Result: max = Optional[5], min = Optional[1]
  ```
These stream methods provide powerful tools for data processing in a clean and efficient way.
