### Chapter 2 Qs
Question 1: Variables and Constants
What is the correct way to declare a constant in Go?
constant Pi = 3.14
const Pi = 3.14
let Pi = 3.14
var Pi = 3.14

Question 2: Short Variable Declaration
Which of the following is a valid short variable declaration in Go?
x int := 42
var x := 42
x := 42
let x = 42

Question 3: Default Values
What is the default value of an uninitialized int variable in Go?
-1
1
0
nil

Question 4: Naming Conventions
Which of the following variable names is invalid in Go?
_variable
9number
variableName
user_name

Question 5: Scope
If a variable is declared within a function, where can it be accessed?
Anywhere in the program
Only inside that function
Inside the function and its child functions
From any file in the same package

Question 6: Type Inference
What will be the type of x in the following declaration?
x := 3.14
float32
float64
int
decimal

Question 7: Multiple Variable Declaration
Which of the following is a valid multiple variable declaration in Go?
var a, b int = 1, 2
a, b := 1, "two"
var a, b = 1, "two"
All of the above

Question 8: Zero Values
Which Go data type has a zero value of false?
bool
int
string
float64

Question 9: Redeclaring Variables
Given the following code snippet, what happens?
x := 10
x := 20
The code compiles and x becomes 20.
The code does not compile due to redeclaration.
The code compiles, but x remains 10.
A runtime error occurs.

Question 10: Conversion Between Types
What is the correct way to convert an int to a float64 in Go?
float(x)
(float64)x
float64(x)
convert(float64, x)
Let me know if you'd like additional questions or practice scenarios!

You said:
1) 2
2) 3
3) 3
4) 2
5) 3
6) 2
7) 4
8) 1
9) 2
10) 3

ChatGPT said:
ChatGPT
Great attempt at answering the questions! Here's a quick review based on Go's conventions and syntax:
✅ Correct! const Pi = 3.14 is the correct way to declare a constant in Go.
✅ Correct! x := 42 is the valid short variable declaration syntax.
✅ Correct! The default value of an uninitialized int is 0.
✅ Correct! 9number is invalid because variable names cannot start with a number.
❌ The correct answer is 2. Variables declared within a function are accessible only inside that function (function scope).
✅ Correct! Go automatically infers float64 for floating-point literals like 3.14.
✅ Correct! All listed options are valid multiple variable declarations.
✅ Correct! The zero value of bool is false.
❌ The correct answer is 2. Redeclaring x in the same scope will cause a compile-time error.
✅ Correct! float64(x) is the proper way to convert an int to a float64.
Final Score: 8/10

### Chapter 3
Question 1: Arrays
Which of the following correctly declares an array of 5 integers in Go?
var arr [5]int
arr := [5]int
var arr = [5]int{}
All of the above

Question 2: Slices
What happens when you append to a slice whose underlying array is full?
The append fails.
A runtime error occurs.
A new larger array is created, and the slice references it.
The underlying array is resized.

Question 3: Maps
Which of the following statements is correct about Go maps?
Keys in a map can be of any type, including slices.
Accessing a non-existent key in a map results in a panic.
The delete function can be used to remove a key-value pair from a map.
Maps need to be manually resized when they grow.

Question 4: Structs
Which of the following is a valid way to initialize a struct in Go?
type Point struct {
    X int
    Y int
}
p := Point{}
p := Point{X: 10, Y: 20}
p := Point{10, 20}
All of the above

Question 5: Strings
What is the result of the following code?
s := "Hello, 世界"
fmt.Println(len(s))
7
9
11
12

Question 6: Runes
What is the type of the elements in a []rune slice?
byte
int
rune
char

Question 7: Bytes
Which of the following is a valid way to create a []byte slice from a string?
b := []byte("example")
b := byte("example")
b := make([]byte, "example")
b := bytes.New("example")

Question 8: Slices Capacity
What is the capacity of the slice s after the following code executes?
arr := [5]int{1, 2, 3, 4, 5}
s := arr[1:4]
2
3
4
5

Question 9: Maps Key Check
How can you check if a key exists in a map?
if key in map
if map[key] != nil
if _, ok := map[key]; ok {}
if map.key != nil

Question 10: Structs and Methods
What happens if you call a method on a struct using a pointer receiver, but you pass the struct by value?
The code does not compile.
The method will panic at runtime.
The method works as expected because Go automatically dereferences the struct.
A new copy of the struct is created, and the method operates on the copy.
Let me know if you'd like me to expand on any specific composite type or provide explanations for the answers!

You said:
1) 4
2) 4
3) 3
4) 3
5) 3
6) 3
7) 3
8) 3
9) 3
10) 1 
ChatGPT said:

ChatGPT
Here's a review of your answers for the composite types questions:
❌ Correct Answer: 1
Only var arr [5]int is valid for declaring an array of 5 integers. Other options are invalid syntax.
❌ Correct Answer: 3
When appending to a slice whose underlying array is full, Go creates a new, larger array and the slice references this new array.
✅ Correct!
The delete function can be used to remove a key-value pair from a map.
❌ Correct Answer: 4
All listed options are valid ways to initialize a struct in Go.
✅ Correct!
The length of "Hello, 世界" is 11 because each non-ASCII character (世 and 界) occupies 3 bytes.
✅ Correct!
The type of elements in a []rune slice is rune.
❌ Correct Answer: 1
The correct way to create a []byte slice from a string is b := []byte("example").
✅ Correct!
The capacity of the slice s is 4, as it includes the elements from index 1 to the end of the array.
✅ Correct!
The correct way to check if a key exists in a map is if _, ok := map[key]; ok {}.
❌ Correct Answer: 3
Go automatically dereferences a struct when you call a method with a pointer receiver, so the method works as expected.
Final Score: 6/10
