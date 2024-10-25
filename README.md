# LS215_computational_thinking

## [L1: List Processing and Functional Abstractions](https://launchschool.com/lessons/bfc761bc/assignments)


### [1. Capstone Introduction](https://launchschool.com/lessons/bfc761bc/assignments/db0064bc)
### [2. Introduction to the Course](https://launchschool.com/lessons/bfc761bc/assignments/9a962c82)
### [3. Passing Functions as Arguments](https://launchschool.com/lessons/bfc761bc/assignments/96acf6be)

#### Abstractions allow Code to specialize

#### Passing Functions as Arguments

#### Behaviour as Arguments to Allow abstractions

### [4. Declarative Programming with Abstractions](https://launchschool.com/lessons/bfc761bc/assignments/d07e9b27)

#### Imperative Style

-  Focusing on the steps of solving the problem.

#### Imperative Style with function abstractions.

#### Iteration Focused Abstraction

#### Filter Abstraction that truly reflects the purpose

#### Declarative programming

### [5. List Processing Abstractions](https://launchschool.com/lessons/bfc761bc/assignments/d2af4ac0)


### [6. Iteration](https://launchschool.com/lessons/bfc761bc/assignments/477b4eea)

- In JS the preferred way to iterate over an element in an array is `forEach`

#### Return Value:

#### Build it to understand it

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

### [7. Filtering / Selection](https://launchschool.com/lessons/bfc761bc/assignments/c6f3935e)

- with `filter`.
- 

### [8. Transformation](https://launchschool.com/lessons/bfc761bc/assignments/68c901d9)

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

### [9. Reducing](https://launchschool.com/lessons/bfc761bc/assignments/32501eac)

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

### [10. Interrogation](https://launchschool.com/lessons/bfc761bc/assignments/c81a7804)

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

### [11. Sort](https://launchschool.com/lessons/bfc761bc/assignments/936f8325)
### [12. Combining Abstractions](https://launchschool.com/lessons/bfc761bc/assignments/6e5fb053)

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

### [13. Functional Abstractions on Objects](https://launchschool.com/lessons/bfc761bc/assignments/37649326)

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

### [14. Practice Problem: Total Square Area](https://launchschool.com/lessons/bfc761bc/assignments/54616106)

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

### [15. Practice Problem: Processing Releases](https://launchschool.com/lessons/bfc761bc/assignments/801985a4)

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

### [16. Practice Problem: Octal](https://launchschool.com/lessons/bfc761bc/assignments/b1e4e00d)

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

### [17. Practice Problem: Anagrams](https://launchschool.com/lessons/bfc761bc/assignments/b3d2a692)

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

### [18. Practice Problem: Formatting Bands](https://launchschool.com/lessons/bfc761bc/assignments/7b314293)

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

### [19. Practice Problem: Class Records Summary](https://launchschool.com/lessons/bfc761bc/assignments/ff1533e4)



### [20. Don't Be Afraid to Use Low Level Abstraction](https://launchschool.com/lessons/bfc761bc/assignments/4f67c44f)



### [21. More Exercises](https://launchschool.com/lessons/bfc761bc/assignments/0772a1d7)
### [22. LS215 Lesson 1 Quiz 1](https://launchschool.com/lessons/bfc761bc/assignments/82333670)

![image](https://github.com/user-attachments/assets/30163f94-c812-4ac6-ac38-72704628ec74)
![image](https://github.com/user-attachments/assets/8a626f87-f12f-4bb8-a7b3-fb209e10de42)

## [String and Text Processing](https://launchschool.com/lessons/08996120/assignments)

1	[String Processing Patterns](https://launchschool.com/lessons/08996120/assignments/da21fd18)

- failed to save these notes.

2	String Methods

- failed to save these notes.

3	Practice Problems: Strings
4	Regular Expressions

5	Reverse a String

### [Acronym](https://launchschool.com/lessons/08996120/assignments/e06e683a)

### [Email Validation](https://launchschool.com/lessons/08996120/assignments/7bb83747)

- This problem took me 2 hours, largely because I didn't take time to understand the problem before starting to code. When will I learn? And the LS solution is depressingly concise.

- My code: 

```javascript
function invalidLocalAddress(local) {
  return (local.split('').filter((char) => /[a-z0-9]/i.test(char)).length !== local.length);
}

function invalidDomainAddress(domain) {

  let domainArray = domain.split('.')
  if (domainArray.length < 2) {return false}
  
  const multipleDots = new RegExp('/\.\./', 'i');
  if (multipleDots.test(domain)) {return false}

  const onlyLetters = new RegExp('[a-z]', 'i');
  const nonLetters = new RegExp('[^a-z]', 'i');

  return domainArray.every((component) => 
    (onlyLetters.test(component)) &&
    (!nonLetters.test(component))
  )
}

function isValidEmail(email) {

  let local = email.split('@')[0];
  let domain = email.split('@')[1];
  
  if (
    !email.split('').includes('@') ||
    invalidLocalAddress(local) ||
    invalidDomainAddress(domain)
    ) {return false};

  return true
}
```

- LS code:

```javascript
function isValidEmail(email) {
  return /^[a-z0-9]+@([a-z]+\.)+[a-z]+$/i.test(email);
}
```

- This regex means:
  - `^` This is the start of the line, from which point we start comparing. Not anywhere in the string.
  - `[a-z0-9]` : This is the local address and it has to contain only letters and numbers (the `i` tag at the end makes these case insensitive.
  - `+` this tells the regex that all this must be followed by the next bit. Just like string concatenation.
  - `@` is just that.
  - I'm not sure I can explain why we need the `+` in front of the `@`, but not after it.
  - `([a-z])+\.)` This says match any number of letters followed by a dot (which as a special character needs to be escaped by the forward slash). The round parentheses mean you can have this as many times as you want, as long as there is a single dot at the end.
  - This must be followed by more letters, so `[a-z]`. As long as this is done once, we can ignore the rest.
  - And the the end of the line `$`.
  

8	Matching Parentheses
### [9	Sentiment Analysis 1](https://launchschool.com/lessons/08996120/assignments/46f6d954)

- Here I learnt that if you use a code block inside the `reduce` function, you must remember to return the value. Blocks do not implicitly return in JS. ALternatively you can forgo the curly braces and do it all in a callback function.

### [10	Sentiment Analysis 2](https://launchschool.com/lessons/08996120/assignments/74d8d8ca)

- That's quite the regex:

```javascript
let positiveRegex = /\bfortunes?\b|\bdream(s|t|ed)?\b|love(s|d)?\b|respect(s|ed)?\b|\bpatien(ce|t)?\b|\bdevout(ly)?\b|\bnobler?\b|\bresolut(e|ion)?\b/gi;
```

### [Mail Count](https://launchschool.com/lessons/08996120/assignments/b425bdee)

- This was a good refresher on how to run code in the browser, I should do this more.
- In this problem I learnt how to create an 'options' object, to determine how to format a date object:

```javascript
     function formatDate(date) {
        let options = { weekday: 'short', year: 'numeric', month: 'short', day: 'numeric' };
        return date.toLocaleDateString('en-US', options)
      };
```

- Also `date.valueOf` returns a number of milliseconds, which can be used for sorting chronologically.
- My solution:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>email-parsing-exercise</title>
  </head>
  <body>
    <script src="https://dbdwvr6p7sskw.cloudfront.net/210/files/email_data_v2.js"></script>
    <script>
      function formatDate(date) {
        let options = { weekday: 'short', year: 'numeric', month: 'short', day: 'numeric' };
        return date.toLocaleDateString('en-US', options)
      };
      function mailCount(emailData) {
        emailArray = emailData.split('##||##')
        datesArray = emailArray.map(email => new Date(email.split(`#/#`)[2])).sort((date1, date2) => date1 - date2)

        console.log(`Count of email ${emailArray.length}.`)
        console.log(`Date Range: ${formatDate(datesArray[0])} - ${formatDate(datesArray[datesArray.length - 1])}`);
      }
      mailCount(emailData);

// console output

// Count of Email: 5
// Date Range: Sat Jun 25 2016 - Thu Aug 11 2016
    </script>
  </body>
</html>
```

- LS solution:

```javascript
  function mailCount(emailData) {
  let emails = emailData.split('##||##');
  let count = emails.length;
  let emailDates = emails.map(email => email.split('#/#')[2]);

  console.log('Count of Email: ' + count);
  console.log('Date Range: ' + displayableDateRange(emailDates));
}

function displayableDateRange(dates) {
  let dateObjects = getDateObjects(dates);
  dateObjects.sort((a, b) => a.valueOf() - b.valueOf());
  return dateObjects[0].toDateString() + ' - ' + dateObjects[dateObjects.length - 1].toDateString();
}

function getDateObjects(dates) {
  return dates.map(date => {
    let dateElements = date.split(' ')[1].split('-');
    let month = parseInt(dateElements[0], 10) - 1;
    let day = parseInt(dateElements[1], 10);
    let year = parseInt(dateElements[2], 10);
    return new Date(year, month, day);
  });
}
```

12	[Code Review: Longest Sentence](https://launchschool.com/lessons/08996120/assignments/ef3b41db)


- I will go over this again when I have a fresh brain.

13	Reference Solution: Longest Sentence
14	More Exercises

- done

15	LS215 Lesson 2 Quiz 1

4/6 - I heavily relied on MDN and ChatGPT, so I need to go over this a few times until these distinctions are clear in my mind. 


Topic	Status
1	The "PEDAC" Problem Solving Process	Not completed
2	PEDAC Video Walkthrough	Not completed
3	An Example Problem: Comparing Version Numbers	Not completed
4	Understand the Problem and Requirements (1)	Not completed
5	Understand the Problem and Requirements (2)	Not completed
6	FAQ on the First Two Steps of the PEDAC Process	Not completed
7	Interview Practice Problems: Asking Questions	Not completed
8	Create Examples / Test Cases	Not completed
9	Work with Data Structure and Algorithm	Not completed
10	Translate Algorithm Steps Into Code	Not completed
11	Run Test Cases To Verify and Debug Code	Not completed
12	Watch Others Code Series	Not completed
13	Problem 1	Not completed
14	Problem 2	Not completed
15	Problem 3	Not completed
16	Problem 4	Not completed
17	Problem 5	Not completed
18	Practice Problem: Swap	Not completed
19	More Exercises	Not completed
20	LS215 Lesson 3 Quiz 1	Not completed
21	Course LS215 Feedback

|  | 1st: John the Baptist | 2nd: deep-dive | 3rd: find/fill gaps |
| :--- | :---: | :---: | :---: | 
| L1 | ? |||
| L2 | ? |||
| L3 | ? |||
