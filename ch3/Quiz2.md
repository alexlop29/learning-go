### 15-Q Multiple Choice Quiz

Quiz: Chapter 3 - Composite Types (Go Programming)
Question 1:

What is a composite type in Go?

A type that combines multiple primitive types into a single unit.
A type that only works with slices and maps.
A type used exclusively for error handling.
A type that cannot hold other types.
Question 2:

Which of the following is NOT a composite type in Go?

Slice
Map
Struct
Rune
Question 3:

What is the default value of a slice in Go?

An empty slice with zero length and capacity
A slice containing one element
nil
An empty slice with a length of 1
Question 4:

Which built-in Go function is used to determine the length of a slice?

cap()
len()
append()
size()
Question 5:

What does the make function do in Go?

Creates a pointer to a value
Creates and initializes slices, maps, or channels
Allocates memory for primitive types
Appends elements to a slice
Question 6:

How can you safely check if a key exists in a Go map?

map[key]
_, ok := map[key]
len(map[key]) > 0
map.hasKey(key)
Question 7:

What happens if you try to access a key that does not exist in a Go map?

A runtime panic occurs
It returns nil
It returns the zero value of the map's value type
The key is automatically added to the map
Question 8:

Which statement is true about Go arrays?

They are dynamic and can grow in size.
They are immutable once created.
Their size must be specified at compile time.
They can hold values of different types.
Question 9:

What is the primary difference between a slice and an array in Go?

Arrays can only store integers, while slices can store any type.
Slices are dynamic, while arrays have a fixed size.
Arrays are passed by reference, while slices are passed by value.
Slices do not support indexing, while arrays do.
Question 10:

How is a struct in Go defined?

struct {}
type MyStruct struct {}
new(struct{})
define struct {}
Question 11:

Which of the following is NOT true about Go structs?

Struct fields can have different types.
Structs support inheritance by default.
A struct can have methods associated with it.
Struct fields can be accessed using the dot (.) operator.
Question 12:

How do you initialize an empty map in Go?

map := make(map[string]int)
map := map[string]int{}
Both of the above
None of the above
Question 13:

What does the append function return when used with slices?

The original slice with elements added
A copy of the slice with elements added
A pointer to the modified slice
A map of the modified elements
Question 14:

What happens if you iterate over a Go map using a for loop?

Keys are returned in sorted order.
Keys are returned in random order.
Keys are returned in the order they were inserted.
A runtime error occurs unless the map is sorted.
Question 15:

Which of the following is true about slices in Go?

The capacity of a slice cannot exceed its length.
Slices cannot share the same underlying array.
Slices are references to an underlying array.
A slice's capacity decreases when elements are appended.
Good luck with the quiz!






You said:
1) A type that combines multiple primitive types into a single unit.
2) Rune
3) nil
4) len()
5) Creates and initializes slices, maps, or channels
6) _, ok := map[key]
7) A runtime panic occurs
8) Their size must be specified at compile time.
9) Slices are dynamic, while arrays have a fixed size.
10) type MyStruct struct {}
11) Structs support inheritance by default.
12) Both of the above
13) A copy of the slice with elements added
14) Keys are returned in the order they were inserted.
15) The capacity of a slice cannot exceed its length.

Correct Answers:
✅
✅
✅
✅
✅
✅
✅
✅
✅
Total correct answers: 9

Incorrect Answers:
❌
❌
❌
❌
❌
❌
Total incorrect answers: 6

Final Score:
9/15
