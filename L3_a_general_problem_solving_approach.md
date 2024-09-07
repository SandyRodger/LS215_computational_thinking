## [1	The "PEDAC" Problem Solving Process	](https://launchschool.com/lessons/28467827/assignments/b9dbce8b)

- Why are we going over this now ?
- Answer : because we're going to do harder problems and need to do more extensive PEDAC.

## [2	PEDAC Video Walkthrough	](https://launchschool.com/lessons/28467827/assignments/c461b845)

### Data:

- The problems are larger, so we'll have more complex data-structures
- Choosing the wrong data-structure can lead to a dead-end.
- It's all about thinking which methods fit your problem. Also, what type of objects will you use.
  - Compound data-structures are also to be considered.
- We don't want to be switching mid-algorithm.

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

A distinct string is a string that is present only once in an array.

Given an array of strings, arr, and an integer, k, return the kth distinct string present in arr. If there are fewer than k distinct strings, return an empty string "".

Note that the result string is the one encountered earliest in the array.

```javascript
distinctString(["d","b","c","b","c","a"], 2); // "a"
```

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

- Will the function always be given precisely 1 argument?
  - if no: How would I handle 0, or more than 1?
- Will the array:
  - only contain integers:
    - If no: what, and what do I do with:
      - Infinity?
      - NaN?
      - String numbers?
      - floats?
      - fractions? (Rational Numbers)
      - etc.
  - Ever be empty?
  - Have a limit in size?
  - Be something other than an array? Like an object?
  - Be sparse? How would I deal with that?
  - What would I do with arrays shorter than 3 elements?

- Questions I missed:
  - Negative numbers
  - `-Infinity`
  - Does the order of the numbers matter?
  - Will there be repeated numbers?

### Problem 3: primeNumberPrinter

- Write a function, primeNumberPrinter, that prints all prime numbers present as substrings in a given string.

```javascript
primeNumberPrinter("a4bc2k13d"); // [2, 13]
```

My questions:

- Input
  - Will there always be 1 argument?
    - What is there's less? More?
  - Will the argument always be a string?
    - What do I do if it is anything else?
  - Will it only contain numbers and alphabetical characters?
  - Are non-number characters to be ignored?
  - Are numbers to always be grouped together, or considered as all possible substrings. For instance is "123" only 123 or can it also be "1", "2", "3", "12" and  "23"
    - If the second is true, can the numbers change their order to form more numbers?
- Output
  - Always an array?
    - what if it's empty?
    - Is there a limit in length?
    - contain only strings?
    - How is this to be printed?
      - To the console?
      - Some other output?

LS questions I missed:

- What if the string contains only non-digits.
- Will the string be any length?
- In what order should the output be listed?
- Can the output contain negative numbers. How am I to deal with `-` (and I suppose `.` as well?)

### Problem 4:

​ Write a function that takes a two-dimensional array as the argument and turns it into a flat array with all duplicated elements removed. Treat numbers and number strings (e.g., 1 and '1') as duplicates, and keep the one that comes first in the result.

```javascript
flattenAndUnique([]); // []
flattenAndUnique([[1, 2, 3], ['3', 4, 5, 'a']]); // [1, 2, 3, 4, 5, 'a']
```

My questions:

- Will there always be only one argument? What to do with more or none?
- Will the input always be an array? If not, how do I handle it?
- Will it always contain subarrays? If not, how do I handle it?
- Will the subarrays ever be empty?
- Will they contain elements other than strings and integers?
- Is the case of the strings to be considered?
- Should I mutate the input?
- Should the orignal order be maintained? If not, how...
- Will strings ever contain both numbers and other charcters? If so, how would I treat these?
- Will the array or subarrays ever be sparse?

LS questions:

- can subarrays contain `NaN`, and if so do I remove duplicates?
- Will siubarrays ever contain objects. Can they be duplicate?

## [8	Create Examples / Test Cases](https://launchschool.com/lessons/28467827/assignments/b6f994f4)

- Writing test cases can help us to generalize our requirements. If we are extrapolating from a single example, this can lead us to create requirements tailored to too narrow a case.
- For this reason it's often good to go back to requirements while writing the test cases.

## [9	Work with Data Structure and Algorithm](https://launchschool.com/lessons/28467827/assignments/cc7a825b)

### Data structure choice

- How do we represent our data so that we can best utilize the built-in methods of the language.

### Algorithms

- This is a breakdown of the requirements. It's close to the original, but using lamnguage much closer to the language of JS.
- After writing your algorithm, it's a good iudea to go back over your test cases to verify that your algorithm will work with all of them. This really reduces the risk of writing buggy code. Super important during interviews.

## [10	Translate Algorithm Steps Into Code	](https://launchschool.com/lessons/28467827/assignments/13c13b92)

- With the algorithm so far, and the steps up to now, the code glides out smoothly.

## [11	Run Test Cases To Verify and Debug Code	](https://launchschool.com/lessons/28467827/assignments/94d20e1e)

## [12	Watch Others Code Series	](https://launchschool.com/lessons/28467827/assignments/e8a0b18e)
## [13	Problem 1	](https://launchschool.com/lessons/28467827/assignments/5e4c3863)

- Too much sniffing - fuck this.

## [14	Problem 2	](https://launchschool.com/lessons/28467827/assignments/8483efc4)

- Skipped 5 mins in. 

## [15	Problem 3	](https://launchschool.com/lessons/28467827/assignments/3e9003a4)

- Skiiiiiiiip

## [16	Problem 4	](https://launchschool.com/lessons/28467827/assignments/a4861db0)

- OK, after having failed the practice problem, I'm eating humble pie and watching a damn video.
- Rememeber to write requirements BEFORE writing your test cases
- You shouldn't need to go back and re-read the problem, because your own rewriting of the requirements should be a comprehensive break-down of the problem.
- "If you feel it's hard to express the requirements then you'll struggle even more with the algorithm, and more with the code. So this is the moment to go back and re-consider the data-structures you've chosen and the mental mdoel you're working with.
- Don't slip into the algorithm (so, no mentioning of methods/functions)
- It is very helpful to speak one's process aloud.
- PART OF CREATING YOUR MENTAL MODEL IS ESTABLISHING THE RIGHT VOCABULARY.

## [17	Problem 5	](https://launchschool.com/lessons/28467827/assignments/d375ac5f)

- FML, 103 minutes?!
- Interesting that it is harder than the interviews.
- "rail fence cipher" - cool name.

## [18	Practice Problem: Swap	](https://launchschool.com/lessons/28467827/assignments/abd935ee)

- I've gotten stuck in my coding. SO maybe I'll go back and wathc those videos...

- Later:
  - My code is way to buggy, and the LS solution much simpler and shorter.
  - I need lots more practice
 
- My solution:

```javascript
function swap(string) {
  if (!string.length) return string;
  
  let inputAsArray = string.split('');
  let lettersRegex = /[a-z]/i;
  let numbersRegex = /[0-9]/;
  let index = 0;
  let numbers = inputAsArray.filter((char) => numbersRegex.test(char));
  let letters = inputAsArray.filter((char) => lettersRegex.test(char));
  let alreadySwapped = {};

  let output = inputAsArray.map((char) => {
    if (alreadySwapped[index]) {
      index += 1
      return alreadySwapped[index-1];
    }
    else if(lettersRegex.test(char) && numbers[0] && !alreadySwapped[index]) {
      index += 1;
      alreadySwapped[string.indexOf(numbers[0])] = char;
      return numbers.shift();
    } else if (numbersRegex.test(char) && letters[0] && !alreadySwapped[index]) {
      index += 1;
      alreadySwapped[string.indexOf(letters[0])] = char;
      return letters.shift();
    } else {
      index += 1;
      return char;
    }
  })

  return output.join('')
}
```

- LS solution:

```javascript
const isLetter = char => /[a-z]/i.test(char);
const isDigit = char => /\d/i.test(char);

function swap(str) {
  if (str.length === 0) return str;

  const chars = str.split("");
  const letters = chars.filter(isLetter);
  const nums = chars.filter(isDigit);

  if (letters.length === 0 || nums.length === 0) return str;

  const swapped = chars.map(char => {
    if (isLetter(char) && nums.length > 0) return nums.shift();
    else if (isDigit(char) && letters.length > 0) return letters.shift();

    return char;
  });

  return swapped.join("");
}
```

## [19	More Exercises	]()
## [20	LS215 Lesson 3 Quiz 1	]()
## [21	Course LS215 Feedback]()
## []()

