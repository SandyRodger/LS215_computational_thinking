# LS215_computational_thinking

## Capstone Introduction
## [Introduction to the Course](https://launchschool.com/lessons/bfc761bc/assignments/9a962c82)
## [Passing Functions as Arguments](https://launchschool.com/lessons/bfc761bc/assignments/96acf6be)

### Abstractions allow Code to specialize

### Passing Functions as Arguments

### Behaviour as Arguments to Allow abstractions

## Declarative Programming with Abstractions

### Imperative Style

-  Focusing on the steps of solving the problem.

### Imperative Style with function abstractions.

### Iteration Focused Abstraction

### Filter Abstraction that truly reflects the purpose

### Declarative programming

## List Processing Abstractions


## [Iteration](https://launchschool.com/lessons/bfc761bc/assignments/477b4eea)

- In JS the preferred way to iterate over an element in an array is `forEach`

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
- 

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



## Practice Problem: Anagrams
## Practice Problem: Formatting Bands
## Practice Problem: Class Records Summary
## Don't Be Afraid to Use Low Level Abstraction
## More Exercises
## LS215 Lesson 1 Quiz 1
![image](https://github.com/user-attachments/assets/30163f94-c812-4ac6-ac38-72704628ec74)
![image](https://github.com/user-attachments/assets/8a626f87-f12f-4bb8-a7b3-fb209e10de42)
