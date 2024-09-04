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

- Input types:
  - Can the function handle different types of inputs (stirngs? Booleans? etc)
- Special Values:
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

## [7	Interview Practice Problems: Asking Questions	]()
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
