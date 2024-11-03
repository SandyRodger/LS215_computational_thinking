## [Interview Practice Problems: Asking Questions](https://launchschool.com/lessons/28467827/assignments/cec18cce)

## My PEDAC:
    
P: Rewrite problem in your own words
    Inputs/Outputs:
    R: rules
    Q: questions & answers

E: Analyse Examples
    T: create test cases ( the interviewer will not be able to answer "have I covered all of the edge cases, but they can tell you if a test should return true or false)

D: 



A: -

A: - with coding terms

C:

T: test cases

### Checklist

- (At each step ask questions and WRITE DOWN THE ANSWERS)

- Read the problem 3 times
- Create a section for Questions
  - Each answer should have a test case written for it.
  - Don't forget to ask if arrays can be sparse.
- Read Question and examples 3 times
  - After the 1st time say to yourself: "It looks easy, as always, but as always there are hidden difficulties"
- Rewrite question in your own words, breaking it down into logical parts.
- Go through all examples noting what they demonstrate and what they don't.
- Data: Does this problem better fit Array's (unordered, use the index) or Objects (access properties directly). Think of which methods might be useful.


- A1: Describe the problem as though it is being done by a baby with letter-blocks.
  - Go back to original question and see if it still fits
- A2: Write out the algorithm again at a high level (abstract)
  - What are the distinct responsabilities?
  - Go back to original question and see if it still fits
- A3: Write the algorithm using coding language (lower level)
  - Include expected outcome at each step
- C: Rewrite the final algorithm in code


### Olly chat:

- cord for jobs

### topics to study:

- Language syntax, types, and flow control
- Functions, variables, and scopes
- Arrays and objects
- Language built-in methods on String and Array
- Mutability of values and objects
- Pure functions and side effects
- Regular expressions (what's covered in our book)

### general problem solving topics you will be expected to demonstrate:

- Be able to build and communicate a clear plan towards solving a given problem
- Fluent with JavaScript's built-in list processing abstractions and higher-order functions
- Be able to write code that follows clear and idiomatic abstractions
- Be able to validate assumptions, debug issues, and fix any problems
- Recognize where and when helper functions can make your job easier
- Good code style

### Interview Study Guide

- This interview is going to assess your basic JavaScript programming and problem solving skills.

- In this interview, you will be expected to follow the process we covered in the last lesson, "A General Problem Solving Approach," to solve a coding challenge. You will have 40 minutes to answer it. It is as follows:
  - Understand the problem
  - Examples/test cases
  - Data structure and algorithms
  - Verify your algorithm against the examples
  - Start coding


### General communication and presence:

- Think, speak, and code deliberately
- Accuracy in concepts and terminologies
- Stay calm

### Things to include in the assessment:

    - save callbacks in different variables, so that the function can adapt to different use cases. Pass functions as arguments.

### Mattic 2.11.24

- Practice questions:
    - https://edabit.com/user/6vfjruFp8ZpRSi3AT
    - https://edabit.com/collection/SjWvg4gA8vpgZnLL7
    - https://edabit.com/collection/QcMwhyqrjLzqupHj4
    - https://ryandej.medium.com/ls216-practice-problems-e68c3df04be4
  - Max 10 test cases
  - Hacker Rank problems
  - Lots of problems to do with Object manipulation
  - Find the flow chart in the course of what to ask when given information.
  - Even with good question asking that reveal the implicit requirements, expect for there to be extra test cases. So expect your solution to be rendered incomplete.
  - (Time limit is soft)
  - People fail because they panic
  - Problem will be surprisingly easy - this is a trap.
  - You may have to do a 2nd pedac - but you can sort of rush it (?)
  - deffo reach out to other students.

### Derek Novak 3.11.24

```javascript
// Create a function that counts the amount of subarrays in a 2D array that contain the same elements as a given array.

// console.log(sameElements([[1, 2, 3], [2, 3, 4], [3, 1, 2]], [1, 2, 3]) === 2);

/*
Questions & answers:

- Do not consider sparse arrays.
- The subarrays in arg1 and the array of arg2 will only contain primitive values.

P:

Write a function which takes 2 arguments (both arrays - possibly 2D)
This function will output an integer reflecting how many subarrays from arg1 contain the same (type and value) elements as the elements in arg2.

Rules:

- I am allowed to mutate the input.

Output:
Integer <
Null if 1st argument is an empty array
If the 2nd arg is empty return the length of the 1st arg.

E:

sameElements([[1, 2, 3], [2, 3, 4], [3, 1, 2]], [1, 2, 3]) === 2;

- sorting logic?

D:

Arrays
looping
helper function: 
  - containsSameElements(array1, array2)

  [[1, 2, 3], [2, 3, 4], [3, 1, 2]] // [1, 2, 3]

[]
testArray = [1, 2, 3]

A:

LOOP: filter nestedArray
  - look at each subarray & pass it into a helper function:

  HELPER FUNCTION: containsSameElements(subArray, testArray)

  - while testArray isn't empty
  - take (and delete) each element from testArray (n)
    - if n is included in subArray
      - delete it from subArray
    - if not 
      - return false

  - return true 

- return the length of the filtered array.

C:
*/

function containsSameElements(subArray, testArray) {

  while (testArray.length) {
    let n = testArray.shift()
    if (subArray.includes(n)) {
      subArray.splice(subArray.indexOf(n), 1);
    } else {
      return false
    }
  }
  return true
}

function sameElements(nestedArray, testArray) {
  if (nestedArray.length === 0) {return null};

  return nestedArray.filter((subArray) => {
    return containsSameElements(subArray, [...testArray]);
  }).length
}

// console.log(containsSameElements([1, 2, 3], [1, 2, 3])); // true
// console.log(containsSameElements([1, 3, 2], [1, 2, 3])); // true
// console.log(containsSameElements([1, 2], [1, 2, 3])); // false
// console.log(containsSameElements([1, 3, 2], [1, 3])); // true
// console.log(containsSameElements([1, 3, 2, 4], [1, 2, 3])); // true

// Happy Path
console.log(sameElements([[1, 2, 3], [2, 3, 4], [3, 1, 2]], [1, 2, 3]) === 2);
// Duplicate 1st arg
console.log(sameElements([[1, 2, 3, 1], [2, 3, 4], [3, 1, 2]], [1, 2, 3]) === 2);
// Primitives
console.log(sameElements([["false"]], [false]) === 0);
console.log(sameElements([["1"]], [1]) === 0);

console.log('-- Additional --')

console.log(sameElements([[1, 2, 3], [2, 3, 4], [3, 1, 2]], [1, 1, 2, 3]) === 0);
console.log(sameElements([[1, 2, 3, 1], [2, 3, 4], [3, 1, 2]], [1, 2, 3]) === 2);
console.log(sameElements([['1', 2, 3], [2, 3, 4], [3, 1, 2]], [1, 2, 3]) === 1);
console.log(sameElements([[null, false, true], ['string', true, true], [false, 29, null]], [null, false]) === 2);
console.log(sameElements([[1, 2, 3], [2, 3, 4], [3, 1, 2]], []) === 3);
console.log(sameElements([[]], [1, 2, 3]) === 0);
console.log(sameElements([], [1, 2, 3]) === null);

Start: 9:10
DS: 9:24
Alg: 9:27
Code: 9:51
End: 10:10

Good:
- I like that you took a mental break and communicated that well
- Great job catching the mistake of not looking at the 2nd test case, then fixing your algorithm accordingly
- Utilized a great higher-level algorithm

Improvements:
- Devise a list of questions to always ask as part of the Problem section
- List all responses in the rules section
    - Create test cases from these
- Create more test cases before moving onto data structure
    - Label the test cases you create
- Play around with the code before constructing an algorithm
- When walking through algorithm, use a test case
- Watch out for missed semi-colons
- Any quick checks you make by altering the code, fix them afterwards so you don't forget
///
