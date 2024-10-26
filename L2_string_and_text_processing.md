
# [String and Text Processing](https://launchschool.com/lessons/08996120/assignments)

## [1. String Processing Patterns](https://launchschool.com/lessons/08996120/assignments/da21fd18)

- Usually follows this pattern:
  - -declare new string/array to be used as a container
  - Break down the string, usually by char, line, sentence, word or delimiters. Remove any unnecessary chars.
  - Apply suitable list-processing strategy.
  - Combine results into new string (if necessary).
- Regex are good for this.
  - Note that Javascript does not have an `x` flag, unlike Ruby. To work around this you need to put a literal space in the group you wish to ignore:
    - `let textArray = text.replace(/[^a-z ]/ig, '').split(' ');`

## [2.	String Methods](https://launchschool.com/lessons/08996120/assignments/deb5d37b)

- `indexOf()`
- `lastIndexOf()`
- `replace()` (returns a new string)
- `split()`
  - remember this will exclude the string used as a seperator.
- `substring()`
  -  remember this will automatically start with the lower argument, regardless of the order of arguments. So:
  -  `string.substring(a, b) === string.substring(b, a);`
-  `toUpperCase()` , `toLowerCase()`

## [3.	Practice Problems: Strings](https://launchschool.com/lessons/08996120/assignments/b674f41e)

- 18 problems ranging from boringly easy to just easy.

Q18: asks for user input

```javascript
const readlineSync = require("readline-sync");
let name = readlineSync.prompt('What is your name?');

if (name.endsWith('!')) {
  name = name.slice(0, -1);
  console.log('HELLO ' + name.toUpperCase() + '. WHY ARE WE SCREAMING?');
} else {
  console.log('Hello ' + name + '.');
}
```


## [4.Regular Expressions](https://launchschool.com/lessons/08996120/assignments/0a36d422)

- Asks you to re-read the Launch School book

## [5.	Reverse a String](https://launchschool.com/lessons/08996120/assignments/27270b8d)

- Easy

## [6. Acronym](https://launchschool.com/lessons/08996120/assignments/e06e683a)

- 2nd go 5 minutes, no pedac.
- Remember it adds to succinctness (though perhaps not readability) to split chained functions into new lines:

```javascript
function acronym(string) {
  return string.replace('-', ' ')
               .split(' ')
               .map((word) => word[0]
               .toUpperCase())
               .join('');
}
```

## [7. Email Validation](https://launchschool.com/lessons/08996120/assignments/7bb83747)

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

##### 2nd go:

- I went in too cocky and got buggy code. Abandoning after an hour. Try again later.

## [8.	Matching Parentheses](https://launchschool.com/lessons/08996120/assignments/bb6d711f)

  - 1st go: 2 hours
  - 2nd go: 1 hour
    - I used a clever regex match method to extract the parentheses, but it didn't actually make the code more succinct. The original solution was 7 lines shorter.
    
## [9	Sentiment Analysis 1](https://launchschool.com/lessons/08996120/assignments/46f6d954)

- Here I learnt that if you use a code block inside the `reduce` function, you must remember to return the value. Blocks do not implicitly return in JS. Alternatively you can forgo the curly braces and do it all in a callback function.

## [10	Sentiment Analysis 2](https://launchschool.com/lessons/08996120/assignments/74d8d8ca)

- That's quite the regex:

```javascript
let positiveRegex = /\bfortunes?\b|\bdream(s|t|ed)?\b|love(s|d)?\b|respect(s|ed)?\b|\bpatien(ce|t)?\b|\bdevout(ly)?\b|\bnobler?\b|\bresolut(e|ion)?\b/gi;
```

## [11. Mail Count](https://launchschool.com/lessons/08996120/assignments/b425bdee)

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

## [12. Code Review: Longest Sentence](https://launchschool.com/lessons/08996120/assignments/ef3b41db)

- I will go over this again when I have a fresh brain.
- In second go through I found that my solution will not cover most of the test suite. This is because I focused on trying to solve the test cases, rather than match the instructions exactly. Having read a few of the solutions I want to allow myself a few days to forget them before attempting a third time and submitting it to be reviewed (26.10.24).

## [13	Reference Solution: Longest Sentence](https://launchschool.com/lessons/08996120/assignments/ef3b41db)


## [14	More Exercises](https://launchschool.com/lessons/08996120/assignments/2986a10c)

- done... once

## [15	LS215 Lesson 2 Quiz 1](https://launchschool.com/lessons/08996120/assignments/dcc8e445)

4/6 - I heavily relied on MDN and ChatGPT, so I need to go over this a few times until these distinctions are clear in my mind. 

- Attempt 2 (26.10.24) :
  - 
