### Questions
Here are 10 multiple-choice questions based on "Composite Types" from Learning Go, 2nd Edition:
Which of the following is a composite type in Go?
a) string
b) int
c) struct
d) float64

How do you declare a slice in Go?
a) var x []int
b) var x int[]
c) var x = new(int[])
d) var x slice[int]

What is the zero value of a slice in Go?
a) nil
b) []
c) {}
d) [0]

How is a map declared in Go?
a) var m map[int]string
b) var m map of int to string
c) map[int]string m
d) let m = map[int, string]

What happens if you try to access a key in a map that doesn’t exist?
a) It throws a runtime error.
b) It returns nil.
c) It returns the zero value of the value type.
d) It returns undefined.

Which of the following is used to create a dynamically sized array in Go?
a) slice
b) array
c) map
d) struct

How do you define a struct in Go?
a) type Person { string Name; int Age }
b) type Person struct { Name string; Age int }
c) struct Person { string Name; int Age }
d) define struct Person (Name: string, Age: int)

Which of the following is NOT true about slices in Go?
a) Slices have a length and capacity.
b) Slices are pointers to arrays.
c) Slices can grow dynamically beyond their capacity.
d) Modifying a slice affects the underlying array.

What does the make function do in Go?
a) It creates new slices, maps, or channels.
b) It initializes a struct.
c) It allocates memory for primitive types.
d) It declares and assigns constants.

How do you append an element to a slice in Go?
a) slice.add(element)
b) slice.push(element)
c) append(slice, element)
d) slice = add(slice, element)

### Answers
1) c
2) a
3) b
4) a
5) b
6) a
7) a
8) d
9) c
10) c

### Analysis
Let's review your answers for the Composite Types questions:
c) struct
Correct! struct is one of the composite types in Go, along with slices, arrays, and maps.
a) var x []int
Correct! This is the proper way to declare a slice in Go.
b) []
Incorrect. The zero value of a slice in Go is nil, not an empty slice. So the correct answer is a) nil.
a) var m map[int]string
Correct! This is the correct syntax to declare a map in Go.
b) It returns nil.
Incorrect. Accessing a key that doesn’t exist in a map returns the zero value of the value type, not nil. The correct answer is c) It returns the zero value of the value type.
a) slice
Correct! A slice is a dynamically sized array in Go.
a) type Person { string Name; int Age }
Incorrect. The correct syntax for defining a struct in Go is b) type Person struct { Name string; Age int }.
d) Modifying a slice affects the underlying array.
Correct! Changes to a slice modify the underlying array because slices are references to the array.
c) It allocates memory for primitive types.
Incorrect. The make function is specifically used for slices, maps, and channels. The correct answer is a) It creates new slices, maps, or channels.
c) append(slice, element)
Correct! This is the correct way to append elements to a slice in Go.

Final Score:
Correct: 6/10
Incorrect: 4/10
Make sure to review Questions 3, 5, 7, and 9. Let me know if you'd like detailed explanations for these!
