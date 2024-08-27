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
## Filtering / Selection
## Transformation
## Reducing
## Interrogation
## Sort
## Combining Abstractions
## Functional Abstractions on Objects
## Practice Problem: Total Square Area
## Practice Problem: Processing Releases
## Practice Problem: Octal
## Practice Problem: Anagrams
## Practice Problem: Formatting Bands
## Practice Problem: Class Records Summary
## Don't Be Afraid to Use Low Level Abstraction
## More Exercises
## LS215 Lesson 1 Quiz 1
