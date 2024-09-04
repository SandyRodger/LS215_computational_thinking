## [1	The "PEDAC" Problem Solving Process	](https://launchschool.com/lessons/28467827/assignments/b9dbce8b)

- Why are we going over this now ?
- Answer : because we're going to do harder problems and need to do more extensive PEDAC.

## [2	PEDAC Video Walkthrough	](https://launchschool.com/lessons/28467827/assignments/c461b845)

- LS solution:

```javascript
function queenCoordinates(board) {
  let coordinates = {};
  board.forEach((row, rowIndex) => {
    if (row.includes('B')) {
      coordinates['B'] = [rowIndex, row.indexOf('B')];
    }

    if (row.includes('W')) {
      coordinates['W'] = [rowIndex, row.indexOf('W')];
    }
  });

  return coordinates;
}

function attackableCoordinates(coord1, coord2) {
  if (coord1[0] === coord2[0]) return true;
  if (coord1[1] === coord2[1]) return true;

  let rowDifference = Math.abs(coord1[0] - coord2[0]);
  let columnDifference = Math.abs(coord1[1] - coord2[1]);
  if (rowDifference === columnDifference) return true;

  return false;
}

function queenAttack(board) {
  board = board.split('\n');

  let queens = queenCoordinates(board);
  if (!('B' in queens && 'W' in queens)) return undefined;

  return attackableCoordinates(queens['B'], queens['W']);
}
```

- Things I failed in my solution:
  - To use/know the `Math.abs` method to find the abolute difference between the rows and columns.
  - To use `.indexOf` to return the index of the queen in the row, without iterating through the whole row.

## [3	An Example Problem: Comparing Version Numbers	]()
## [4	Understand the Problem and Requirements (1)	]()
## [5	Understand the Problem and Requirements (2)	]()
## [6	FAQ on the First Two Steps of the PEDAC Process	](https://launchschool.com/lessons/28467827/assignments/c461b845)

### Can I ever skip the P ?

- No (I think - it's not explicitly stated), but the amount of time spent here depends on the complexity of the problem. It's about translating the problem into:
  - definitions
  - rules
- Ask yourself: 'are the requirements already given as "technical terms" or only demonstrated. What is expressed as a higher problem domain or do they contain implicit knowledge that needs to be teased out?

### Where to begin ?

- Inputs and outputs
- Then definitions and rules. What needs to be more clearly defined? 

### What is a test case ?

- Include input and output
- two types:
  - generic
  - edge cases: special handling

### How do I write good ones

- **Input types:**
  - Can the function handle different types of inputs (stirngs? Booleans? etc)
- **Special Values:**
  - If the input is a ...
    - Number, does it work with:
      -  0?
      -  negative ints?
      -  fractions?
      -  `NaN` ?
      -  `infinity` ?
    - String, does it work with
      -  empty strings ?
      -  Array?
      -  Object?
    -  Array, does it work with:
      -  sparse arrays?
      -  arrays with object properties?
-  **Valid/invalid inputs:**
  -  What should we consider invalid? And what should we do with them ?
    -  For example if we're told the input is a "word", can it have non-letter chars?
    -  Should we rteturn a `null` or `undefined` if it's invalid?
    -  Should we consider letter case?
    - what if input is omitted?
      - Have a default parameter?
      - Raise an exception?
      - return a specific value?
- Cover these as completely as possible. generic and edge cases.
- Remember: conditional requirements need test cases that cover both sides of the condition.
- Avoid testing more than one requirement per test-case. This will make debugging easier.
  - In fact you can have more than one test-case for a single requirement. That's good.

### Test cases:

- A great life-skill. For instance, when a client gives you a vague brief.

### Do I always need to consider every possible edge case?

- Depends on the sitch:
  - If the function is part of a larger program and we know the input will always be a string, then it's ok to ignore other inputs.
  - If we're uncertain of the input types, then we need to be quite careful.
  - Making assumptions about what the input will be, without asking the interviewer questions can be a costly mistake.

### Why is it important to create examples before we work through the algorithm?

1. Creating test cases forces us to understand the problem requirements
2. It may highlight gaps in our requirements section. It is better to fix these things earlier.
3. Test cases provide an end to the problem. If they all pass we know we're done. If the test cases are incomplete, the problem may not be solved and by the time you realise it will be too late.
4. An interviewer may not be abkle to anser a vague question like, 'have i covered all the edge cases', but they can say whether a specific case is to be considered.
5. It's good in interviews. it allows a chance to communicate with the interviewer.



## [7	Interview Practice Problems: Asking Questions	](https://launchschool.com/lessons/28467827/assignments/cec18cce)

- Here we practice identifying what questions we should ask the interviewer before starting the problem.
- Don't forget follow-up questions. An answer to one question can raise more questions.
- Identify as many unstated requirements as possible.

### Problem 1: Distinct strings:

- My questions:
  - Will 2 arguments always be provided?
  - Will the strings ever be:
    - longer than 1 character?
    - empty?
    - Will the strings only be alphabetical characters?
    - Will the array ever be empty?
  - Will the integer ever be negative, and if so is that meant to denote spaces from the end?
- Questions I missed:
  - What should I do if an argument is omitted?
  - What should I do if more than 2 arguments are given?
  - Will the first argument always be an array? If not, what do I do?
  - Will the second argument always be an integer? If not, what do I do?
  - Can an array be sparse? How would I treat the missing elements?
  - Can an array contain any number of elements?

### Problem 2: third largest num

- Given an array of integers, nums, return the third largest number in the array. If the third largest number does not exist, return the greatest number.

- You are not allowed to sort the array.

```
thirdMax([3, 2, 1]); // 1
```

My questions:

- 

## [8	Create Examples / Test Cases	]()
## [9	Work with Data Structure and Algorithm	]()
## [10	Translate Algorithm Steps Into Code	]()
## [11	Run Test Cases To Verify and Debug Code	]()
## [12	Watch Others Code Series	]()
## [13	Problem 1	]()
## [14	Problem 2	]()
## [15	Problem 3	]()
## [16	Problem 4	]()
## [17	Problem 5	]()
## [18	Practice Problem: Swap	]()
## [19	More Exercises	]()
## [20	LS215 Lesson 3 Quiz 1	]()
## [21	Course LS215 Feedback]()
## []()
![image](https://github.com/user-attachments/assets/2c4772a4-c49d-48f1-bc27-f46f03d566b6)
