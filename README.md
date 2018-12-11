# DSA Notes
My notes from Ray Wenderlich's Data Structures and Algorithms book

## Table of Contents

* [Time Complexity](#time-complexity)
  * [Constant Time](#constant-time)
  * [Linear Time](#linear-time)
  * [Quadratic Time](#quadratic-time)

## Time Complexity

Time complexity is a measure of the time required to run an algorithm as the number of inputs increase. It only gives a high-level overview of the performance, so loops that happen a set number of times or other setup code is not part of the basic calculation. All constants are dropped in the final notation.

### Constant Time

An algorithm that has the same running time regardless of the size of the input. The Big O notation is O(1).

**Example:**

The size of the array has no effect on the running time, because it just checks the first element of the array.

```swift
func checkFirst(names: [String]) {
    if let first = names.first {
    print(first)
  } else {
    print("no names")
  }
}
```

### Linear Time

An algorithm where the running time increases linearly based on the size of the input. The Big O notation is O(n).

**Example:**

The size of the array has no effect on the running time, because it just checks the first element of the array.

```swift
func printAllNames(names: [String]) {
    for name in names {
      print(name)
    }
}
```

### Quadratic Time

An algorithm that takes the running time proportional to the square of the input size. The Big O notation is O(n^2).

**Example:**

The function prints out all the names for every name in the array. So if you have 5 names, it'll print the 5 names 5 times for a total of 25 print statements.

```swift
func printAllNames(names: [String]) {
    for _ in names {
      for name in names {
        print(name)
      }
    }
}
```

