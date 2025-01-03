
## Capstone Introduction
## [Introduction to the Course](https://launchschool.com/lessons/bfc761bc/assignments/9a962c82)

- Here we separate the 2 major parts of coding:
  - Understanding the problem and building a mental model of it.
  - Write the model out in code.
- In LS_215 we're concentrating on the first part.
- This course covers:
  - Thinking logically: analyzing the problem and solutions paths.
    - Centre and edge cases.
  - Thinking procedurally and the bottom up imperative solution expressions.
  - Thinking top-down, declarative solution expressions.

## [Passing Functions as Arguments](https://launchschool.com/lessons/bfc761bc/assignments/96acf6be)

- Functions are:
  - first-class objects
  - lists of statements that can have parameters whose values dictate some aspect of their behaviour.

### Abstractions allow Code to specialize

- ORGANIZE CODE BY PURPOSE AND RESPONSIBILITY

### Passing Functions as Arguments

- An example where the callback function is saved in a variable, the array in another variable and the main function in another variable. So when they are combined in the calling of the function each part can be provided without depending on the other parts.

### Behaviour as Arguments to Allow abstractions

- If you are only able to pass objects to methods then your function can only do a specific task. But if you can pass functions then your function becomes an abstraction. You can say "iterate through an array and do something"

## Declarative Programming with Abstractions

### Imperative Style

-  Focusing on the steps of solving the problem without saving any of the funtionality in variables to abstract it away.

### Imperative Style with function abstractions.

- Using descriptive variable names to store some of the functionality, so the developer doen't have to figure out whaat the code is doing. Rather he just reads something like "isOdd" and understands that this piece of code will return a boolean based on whether the input is odd or not.

### Iteration Focused Abstraction

- Like the last one, but using JS' built in iterators so we don't have to think about it.

### Filter Abstraction that truly reflects the purpose

- Using filter in a way that mirrors the reality of the problem:

```javascript
let array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let oddNumbers = array.filter(isOddNumber);

console.log(oddNumbers);

function isOddNumber(number) {
  return number % 2 === 1;
}
```

- Remember to use filter when you're using a function expression to call another function.
- This is an expression of the problem that is close to how a human would describe and think about the problem. Our resulting code is:
  - More readable (because it is better fitting the mental model)
  - More concise
  - More robust (because we use the built-in abstraction `filter` rather than building our own.

### Declarative programming

- The higher the level of abstraction, the more declarative it will be.
- Declarative programming frees devs to think on a human level. By contrast, imperative programing means you have to imagine yourself as a computer.
- Built your own abstractions to "push-down" implementation details.

## [List Processing Abstractions](https://launchschool.com/lessons/bfc761bc/assignments/d2af4ac0)

- Iteration:
  - `forEach()`
- Filter/selection:
  - `filter()`
- Transformation:
  - `map()`
- Ordering:
  - `sort()`
- Reducing:
  - `reduce()` , `reduceRight()`
- Interrogation:
  - `every()` , `some()`

## [Iteration](https://launchschool.com/lessons/bfc761bc/assignments/477b4eea)

- In JS the preferred way to iterate over an element in an array is `forEach`. (Isn't that for loops?)

### Return Value:

### Build it to understand it

```javascript
function myForEach(array, func) {
  for (i = 0; i <= array.length; i += 1) {
    func(array[i])
  }
}

let min = Infinity;
let getMin = value => (min = value <= min ? value : min);
myForEach([4, 5, 12, 23, 3], getMin);
console.log(min);                        // 3

// LS solution:

let min = Infinity
let max = -Infinity

let getMinMax = function (value) {
  if (value >= max) {
    max = value;
  }

  if (value <= min) {
    min = value;
  }
};

[4, 5, 12, 23, 3].forEach(getMinMax);

console.log(min, max);
```

## [Filtering / Selection](https://launchschool.com/lessons/bfc761bc/assignments/c6f3935e)

- with `filter`.
- If the return value of the callback is truthy it will be included in the new array otherwise not.
- `Math.pow()`

## [Transformation](https://launchschool.com/lessons/bfc761bc/assignments/68c901d9)

```javascript
function myMap(array, func) {
  let output = [];
  array.forEach((object) => output.push(func(object)))
  return output;
}

let plusOne = n => n + 1;
let t = myMap([1, 2, 3, 4], plusOne);       // [ 2, 3, 4, 5 ]
console.log(t)
```

## [Reducing](https://launchschool.com/lessons/bfc761bc/assignments/32501eac)

```javascript
function myReduce(array, func, initial) {
  let output = initial ? initial : [array[0]]
  array.forEach((num) => output = func(output, num))
  return output
}

let smallest = (result, value) => (result <= value ? result : value);
let sum = (result, value) => result + value;

console.log(myReduce([5, 12, 15, 1, 6], smallest));           // 1
console.log(myReduce([5, 12, 15, 1, 6], sum, 10));            // 49

// LS solution:

// function myReduce(array, func, initial) {
//   let value;
//   let index;

//   if (initial === undefined) {
//     value = array[0];
//     index = 1;
//   } else {
//     value = initial;
//     index = 0;
//   }

//   array.slice(index).forEach(element => value = func(value, element));
//   return value;
// }
```

## [Interrogation](https://launchschool.com/lessons/bfc761bc/assignments/c81a7804)

- `Array.prototype.some` and `Array.prototype.every`

```javascript
function myOwnEvery(array, func) {
  array.forEach((element) => {
    if (!func(element)) {
      return false
    }
  })
  return true
}

let isAString = value => typeof value === 'string';
console.log(myOwnEvery(['a', 'a234', '1abc'], isAString));       // true
```

- When you use return false inside the forEach callback, it only exits the current callback function, not the entire myOwnEvery function.

## [Sort](https://launchschool.com/lessons/bfc761bc/assignments/936f8325)
## [Combining Abstractions](https://launchschool.com/lessons/bfc761bc/assignments/6e5fb053)

```
let names = ['Heather', 'Gisella', 'Katsuki', 'Hua', 'Katy', 'Kathleen', 'Otakar'];
let letters = names.map(name => name[0]);
// letters is [ "H", "G", "K", "H", "K", "K", "O" ]

let counts = letters.reduce((obj, letter) => {
  obj[letter] = obj[letter] || 0;  // set obj[letter] to 0 if it doesn't have a value
  obj[letter] += 1;
  return obj;
}, {});

// counts is { H: 2, G: 1, K: 3, O: 1 }

console.log(counts)
```

## [Functional Abstractions on Objects](https://launchschool.com/lessons/bfc761bc/assignments/37649326)

- `Object.keys`

```
// map to a new object with values doubled from myObject
function doubleObjectValues(object) {
  let objEntries = Object.entries(object);
  let objMapped = objEntries.map(([key, val]) => [key, val * 2]);

  return Object.fromEntries(objMapped);
}

console.log(doubleObjectValues({ a: 1, b: 2, c: 3 })); // { a: 2, b: 4, c: 6 }
```

```
// filter an object to select only values with even numbers
function keepEvenValues(object) {
  let objEntries = Object.entries(object);
  let objFiltered = objEntries.filter(([key, val]) => val % 2 === 0);

  return Object.fromEntries(objFiltered);
}

console.log(keepEvenValues({ a: 1, b: 2, c: 3 })); // { b: 2 }
```

## Practice Problem: Total Square Area

```javascript
function totalSquareArea(array) { 
  let onlySquares = rectangles.filter((subArray) => subArray[0] === subArray[1])
  return totalArea(onlySquares)
}

function totalArea(array) {
  let totals = array.map((square) => square[0] * square[1])
  return totals.reduce((previousValue, total) => previousValue + total)
}

let rectangles = [[3, 4], [6, 6], [1, 8], [9, 9], [2, 2]];

console.log(totalSquareArea(rectangles));    // 121
```

## Practice Problem: Processing Releases

```javascript
function processReleaseData(data) {
  let filteredEntries = data.filter((obj) => obj['id'] && obj['title'])
  return filteredEntries.map((entry) => ({id: entry['id'], title: entry['title'],}))
  // OR
  // return filteredEntries.map((entry) => { return {id: entry['id'], title: entry['title'],}})
}

let t = processReleaseData(newReleases);
console.log(t); // [{ id: 70111470, title: 'Die Hard'}, { id: 675465, title: 'Fracture' }];
```

## [Practice Problem: Octal](https://launchschool.com/lessons/bfc761bc/assignments/b1e4e00d)

```javascript
function octalToDecimal(numberString) {
  let chars = numberString.split('')
  let output = 0
  let power = 0

  for (let i = (chars.length - 1); i >= 0; i -= 1) {
    output += (Number(chars[i])) * (8 ** power)
    power += 1
  }

  return output
}
```

## [Practice Problem: Anagrams](https://launchschool.com/lessons/bfc761bc/assignments/b3d2a692)

```javascript
function isAnagram(candidate, word) {
  let sortedCandidate = candidate.split('').sort()
  let sortedWord = word.split('').sort()
  for (i = 0; i <= sortedWord.length; i += 1) {
    if (sortedCandidate[i] !== sortedWord[i]) {
      return false
    }
  }
  return true
}

function anagram(word, list) {
  return list.filter((candidate) => isAnagram(candidate, word))
}


console.log(anagram('listen', ['enlists', 'google', 'inlets', 'banana']));  // [ "inlets" ]
console.log(anagram('listen', ['enlist', 'google', 'inlets', 'banana']));   // [ "enlist", "inlets" ]
```

- LS solution uses `every` cleverly

## Practice Problem: Formatting Bands

```
let bands = [
  { name: 'sunset rubdown', country: 'UK', active: false },
  { name: 'women', country: 'Germany', active: false },
  { name: 'a silver mt. zion', country: 'Spain', active: true },
];

function capitalizeSentence(sentence) {
  return sentence.split(' ').map((word) => word[0].toUpperCase() + word.slice(1)).join(' ')
}

function removeDots(sentence) {
  let letters = sentence.split('')
  let output = ''
  for (i = 0; i < letters.length; i += 1) {
    if (letters[i] !== '.') {
      output += letters[i]
    }
  } 
  return output
}

function processBands(data) {
  console.log(data[0].name)
  return data.map((entry) => {
    return {
      name: capitalizeSentence(removeDots(entry.name)),
      country: 'Canada',
      active: entry.active,
    }
  }
  )
}

console.log(processBands(bands));

// should return:
[
  { name: 'Sunset Rubdown', country: 'Canada', active: false },
  { name: 'Women', country: 'Canada', active: false },
  { name: 'A Silver Mt Zion', country: 'Canada', active: true },
]
```

- I should have used `band.name = band.name.replace(/\./g, '');`

## [Practice Problem: Class Records Summary](https://launchschool.com/lessons/bfc761bc/assignments/ff1533e4)

## [Don't Be Afraid to Use Low Level Abstraction](https://launchschool.com/lessons/bfc761bc/assignments/4f67c44f)

## [More Exercises](https://launchschool.com/lessons/bfc761bc/assignments/0772a1d7)
## [LS215 Lesson 1 Quiz 1](https://launchschool.com/lessons/bfc761bc/assignments/82333670)
