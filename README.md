# DSA Notes
My notes from Ray Wenderlich's Data Structures and Algorithms book

## Table of Contents

* [Time Complexity](#time-complexity)
  * [Constant Time](#constant-time)
  * [Linear Time](#linear-time)
  * [Quadratic Time](#quadratic-time)
  * [Logarithmic Time](#logarithmic-time)

## Time Complexity

Time complexity is a measure of the time required to run an algorithm as the number of inputs increase. It only gives a high-level overview of the performance, so loops that happen a set number of times or other setup code is not part of the basic calculation. All constants are dropped in the final notation. Some algorithms use each element (linear, quadratic), but some only need to use a subset of elements which lead to a faster runtime (logarithmic,

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

An algorithm where the running time is proportional to the square of the input size. It is one of the worst time complexities to have. The Big O notation is O(n^2).

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




### Logarithmic Time

An algorithm where as the size of the inputs increase, the time it takes to execute increases at a slow rate. This could be done by reducing the amount of comparisons you need to do (like halving the data in a Binary search). The Big O notation is O(log n).

**Example:**

The function only checks half of the array to come up with the answer. It checks the middle value and decides whether it will look at the next values (values to the right on a number line) or previous values (values to the left).

```swift
func naiveContains(_ value: Int, in array: [Int]) -> Bool {
 guard !array.isEmpty else { return false }
 let middleIndex = array.count / 2
 
 if value <= array[middleIndex] {
  for index in 0...middleIndex {
   if array[index] == value {
    return true
   }
  }
 } else {
  for index in middleIndex..<array.count {
   if array[index] == value {
   return true
   }
  }
 }
 
 return false
}
```











