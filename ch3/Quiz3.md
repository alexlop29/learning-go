### Multiple Choice Quiz: Chapter 3 - Composite Types (Go)

Question 1
What is the zero value of a slice in Go?
A) nil
B) []
C) [0]
D) false

Question 2
Which of the following is a correct way to declare an array in Go?
A) var arr = [5]int{1, 2, 3}
B) arr := [5]int{1, 2, 3}
C) arr := [...]int{1, 2, 3}
D) All of the above

Question 3
How are slices different from arrays in Go?
A) Slices have a fixed length, while arrays are resizable
B) Slices are references to an underlying array, while arrays are fixed-size
C) Arrays are always zero-initialized, while slices are not
D) Arrays are not a composite type, but slices are

Question 4
What happens if you try to access an index out of bounds in an array?
A) Returns nil
B) Causes a panic
C) Returns 0
D) No operation is performed

Question 5
Which function is used to append elements to a slice?
A) add()
B) append()
C) concat()
D) insert()

Question 6
How can you get the length of a slice or array in Go?
A) size(slice)
B) len(slice)
C) slice.length()
D) capacity(slice)

Question 7
What will make([]int, 3, 5) do?
A) Create a slice with length 3 and capacity 5
B) Create a slice with 5 elements, initialized to 3
C) Create an array of size 3 and 5 slices
D) Create a slice with 5 elements

Question 8
Which Go composite type does not guarantee key order during iteration?
A) Arrays
B) Slices
C) Maps
D) Strings

Question 9
How do you delete a key-value pair from a map in Go?
A) delete(map)
B) delete(map, key)
C) remove(map, key)
D) map.delete(key)

Question 10
Which of the following is true about structs in Go?
A) Structs can contain only exported fields
B) Structs are mutable by default
C) Struct fields must all have the same type
D) Structs are automatically garbage collected

Question 11
What is the output of cap([]int{1, 2, 3})?
A) 3
B) 0
C) 5
D) Undefined

Question 12
How do you declare a map with string keys and integer values?
A) var m map[string]int
B) m := make(map[string]int)
C) m := map[string]int{}
D) All of the above

Question 13
What happens if you try to read a value from a map with a non-existent key?
A) Returns nil
B) Returns zero value of the value type
C) Causes a runtime error
D) Skips the operation

Question 14
How do you initialize a struct in Go?
A) var s struct{name string}
B) s := struct{name string}{"Go"}
C) s := struct{name string}{name: "Go"}
D) All of the above

Question 15
Which method copies elements from one slice to another in Go?
A) copy()
B) append()
C) move()
D) transfer()

Let me know if you want to verify the answers or need explanations for any of the questions!

You said:
1) nil
2) all of the above
3) Slices are references to an underlying array, while arrays are fixed-size
4) Returns nil
5) append()
6) len(slice)
7) Create a slice with length 3 and capacity 5
8) Maps
9) delete(map, key)
10) Structs are mutable by default
11) 3
12) All of the above
13)  Causes a runtime error
14)  All of the above
15) copy()
ChatGPT said:

ChatGPT
Here are corrections for your answers based on Go concepts:
Correct: nil
Correct: All of the above
Correct: Slices are references to an underlying array, while arrays are fixed-size
Incorrect: Causes a panic (Accessing an index out of bounds in an array results in a runtime panic in Go.)
Correct: append()
Correct: len(slice)
Correct: Create a slice with length 3 and capacity 5
Correct: Maps
Correct: delete(map, key)
Correct: Structs are mutable by default
Correct: 3
Correct: All of the above
Incorrect: Returns zero value of the value type (Accessing a non-existent key in a map does not cause a runtime error but instead returns the zero value of the map's value type.)
Correct: All of the above
Correct: copy()
You got 13/15 correct! Let me know if you need any explanations or further clarification on the incorrect ones.
