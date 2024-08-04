
# String

## Initialization Techniques
```java
        String str1 = "Hello, World!"; // String literal
        String str2 = new String("Hello, Java!"); // Using the new keyword
        char[] charArray = {'H', 'e', 'l', 'l', 'o'};
        String str3 = new String(charArray); // From char array
```

## String Method Demonstration

### `str.length()`
```java
// Length of the string
System.out.println("Length of str1: " + str1.length());
```

### `str.charAt(INDEX)`
```java
// Character at a specific index
System.out.println("Character at index 1 in str1: " + str1.charAt(1));
```

### `str.substring(int beginIndex)`
```java
// Substring
System.out.println("Substring from index 7 in str1: " + str1.substring(7));
```

### `str.substring(int beginIndex, int endIndex)`
```java
// Substring
System.out.println("Substring from index 7 to 12 in str1: " + str1.substring(7, 12));
```

### `str.concat(String str)`
```java
// Concatenation
String str4 = str1.concat(" Let's learn Java.");
System.out.println("Concatenated string: " + str4);
```

### `str.contains(CharSequence s)`
```java
// Contains
System.out.println("Does str1 contain 'World'? " + str1.contains("World"));
```

### `str.equals(Object anObject)`
```java
// Equals
System.out.println("Is str1 equal to str2? " + str1.equals(str2));
```

### `str.equalsIgnoreCase(String anotherString)`
```java
// Equals ignore case
System.out.println("Is str1 equal to 'hello, world!' ignoring case? " + str1.equalsIgnoreCase("hello, world!"));
```

### `str.compareTo(String anotherString)`
```java
// Compare
System.out.println("Comparing str1 and str2: " + str1.compareTo(str2));
```

### `str.startsWith(String prefix)`
```java
// Starts with
System.out.println("Does str1 start with 'Hello'? " + str1.startsWith("Hello"));
```

### `str.endsWith(String suffix)`
```java
// Ends with
System.out.println("Does str1 end with 'World!'? " + str1.endsWith("World!"));
```

### `str.indexOf(String str)`
```java
// Index of
System.out.println("Index of 'World' in str1: " + str1.indexOf("World"));
```

### `str.lastIndexOf(String str)`
```java
// Last index of
System.out.println("Last index of 'o' in str1: " + str1.lastIndexOf("o"));
```

### `str.replace(CharSequence target, CharSequence replacement)`
```java
// Replace
System.out.println("Replacing 'World' with 'Java' in str1: " + str1.replace("World", "Java"));
```

### `str.trim()`
```java
// Trim
String str5 = "   Hello, World!   ";
System.out.println("Trimmed string: '" + str5.trim() + "'");
```

### `str.toUpperCase()`
```java
// To Upper Case
System.out.println("str1 in uppercase: " + str1.toUpperCase());
```

### `str.toLowerCase()`
```java
// To Lower Case
System.out.println("str1 in lowercase: " + str1.toLowerCase());
```

### `str.split(String regex)`
```java
// Split
String[] words = str1.split(" ");
System.out.println("Words in str1:");
for (String word : words) {
    System.out.println(word);
}
```

### `String.join(CharSequence delimiter, CharSequence... elements)`
```java
// Join
String joinedString = String.join(", ", "Java", "Python", "C++");
System.out.println("Joined string: " + joinedString);
```

### `String.format(String format, Object... args)`
```java
// Format
String formattedString = String.format("My name is %s and I am %d years old.", "Alice", 30);
System.out.println("Formatted string: " + formattedString);
```

### `String.valueOf(int i)`
```java
// Value of
int number = 100;
String strNumber = String.valueOf(number);
System.out.println("String representation of number: " + strNumber);
```

### `str.isEmpty()`
```java
// Is Empty
String emptyString = "";
System.out.println("Is emptyString empty? " + emptyString.isEmpty());
```



# Array Methods Demonstration in Java

## Array Initialization Techniques

### Using Array Literals
```java
int[] arr1 = {1, 2, 3, 4, 5}; // Array literal
```

### Using the `new` Keyword
```java
int[] arr2 = new int[5]; // Using the new keyword
arr2[0] = 1;
arr2[1] = 2;
arr2[2] = 3;
arr2[3] = 4;
arr2[4] = 5;
```

## Array Methods Demonstration

### `arr.length`
```java
// Length of the array
System.out.println("Length of arr1: " + arr1.length);
```

### `Arrays.toString(arr)`
```java
import java.util.Arrays;

// Convert array to string
System.out.println("Array as String: " + Arrays.toString(arr1));
```

### `Arrays.sort(arr)`
```java
import java.util.Arrays;

// Sorting the array
int[] arr3 = {5, 3, 4, 1, 2};
Arrays.sort(arr3);
System.out.println("Sorted array: " + Arrays.toString(arr3));
```

### `Arrays.binarySearch(arr, key)`
```java
import java.util.Arrays;

// Binary search in the array
int index = Arrays.binarySearch(arr1, 3);
System.out.println("Index of element '3' in arr1: " + index);
```

### `Arrays.copyOf(arr, newLength)`
```java
import java.util.Arrays;

// Copying the array
int[] arr4 = Arrays.copyOf(arr1, 10);
System.out.println("Copied array with new length: " + Arrays.toString(arr4));
```

### `Arrays.copyOfRange(arr, from, to)`
```java
import java.util.Arrays;

// Copying a range of the array
int[] arr5 = Arrays.copyOfRange(arr1, 1, 4);
System.out.println("Copied range of array: " + Arrays.toString(arr5));
```

### `Arrays.fill(arr, value)`
```java
import java.util.Arrays;

// Filling the array
int[] arr6 = new int[5];
Arrays.fill(arr6, 1);
System.out.println("Filled array: " + Arrays.toString(arr6));
```

### `Arrays.equals(arr1, arr2)`
```java
import java.util.Arrays;

// Comparing arrays
boolean isEqual = Arrays.equals(arr1, arr2);
System.out.println("Are arr1 and arr2 equal? " + isEqual);
```

### `Arrays.asList(arr)`
```java
import java.util.Arrays;
import java.util.List;

// Converting array to list
List<Integer> list = Arrays.asList(arr1[0], arr1[1], arr1[2], arr1[3], arr1[4]);
System.out.println("Array as list: " + list);
```

### `Arrays.stream(arr)`
```java
import java.util.Arrays;

// Creating a stream from the array
int sum = Arrays.stream(arr1).sum();
System.out.println("Sum of elements in arr1: " + sum);
```

### `str.intern()`
```java
// Intern
String str6 = new String("Interned String").intern();
System.out.println("Interned string: " + str6);
```

# ArrayList Methods Demonstration in Java

## ArrayList Initialization

### Importing the ArrayList Class
```java
import java.util.ArrayList;
```

### Creating an ArrayList<>
```java
ArrayList<String> list = new ArrayList<>();
```

### Adding Elements 
```java
// Adding elements to the ArrayList
list.add("Apple");
list.add("Banana");
list.add("Cherry");
```

## ArrayList Method demonstration

### `list.size()`
```java
// Size of the ArrayList
System.out.println("Size of the list: " + list.size());
```

### `list.get(int index)`
```java
// Get element at a specific index
System.out.println("Element at index 1: " + list.get(1));
```

### `list.set(int Index, E element)`
```java
// Set element at a specific index
list.set(1, "Blueberry");
System.out.println("Element at index 1 after update: " + list.get(1));
```

### `list.remove(int Index)`
```java
// Remove element at a specific index
list.remove(1);
System.out.println("List after removing element at index 1: " + list);
```

### `list.contains(Object o)`
```java
// Check if the list contains a specific element
boolean containsApple = list.contains("Apple");
System.out.println("Does the list contain 'Apple'? " + containsApple);
```

### `list.indexOf(Object o)`
```java
// Get the index of a specific element
int index = list.indexOf("Cherry");
System.out.println("Index of 'Cherry': " + index);
```

### `list.isEmpty()`
```java
// Check if the list is empty
boolean isEmpty = list.isEmpty();
System.out.println("Is the list empty? " + isEmpty);
```

### `list.clear()`
```java
// Check if the list is empty
boolean isEmpty = list.isEmpty();
System.out.println("Is the list empty? " + isEmpty);
```

### `list.addAll(Collection<? extends E> c)`
```java
// Add all elements from another collection
ArrayList<String> anotherList = new ArrayList<>();
anotherList.add("Date");
anotherList.add("Elderberry");
list.addAll(anotherList);
System.out.println("List after adding another collection: " + list);
```

### `list.removeAll(Collection<? extends E> c)`
```java
// Remove all elements that are also in another collection
list.removeAll(anotherList);
System.out.println("List after removing another collection: " + list);
```

### `list.retailAll(Collection<? extends E> c)`
```java
// Retain only elements that are also in another collection
list.add("Apple");
list.add("Banana");
list.retainAll(anotherList);
System.out.println("List after retaining another collection: " + list);
```

## Iterating over a list
### Using `for` loop
```java
// Using a for loop
System.out.println("Iterating using a for loop:");
for (int i = 0; i < list.size(); i++) {
    System.out.println(list.get(i));
}
```

### Using an enhanced loop
```java
// Using an enhanced for loop
System.out.println("Iterating using an enhanced for loop:");
for (String fruit : list) {
    System.out.println(fruit);
}
```

### Using an `Iterator`
```java
import java.util.Iterator;

// Using an iterator
System.out.println("Iterating using an iterator:");
Iterator<String> iterator = list.iterator();
while (iterator.hasNext()) {
    System.out.println(iterator.next());
}
```

### Using ***Lambda*** Expression
```java
// Using a lambda expression
System.out.println("Iterating using a lambda expression:");
list.forEach(fruit -> System.out.println(fruit));
```


