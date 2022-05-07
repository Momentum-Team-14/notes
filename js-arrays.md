# JavaScript Arrays

## Arrays

An array is a list of values. These values can be anything, including other arrays. They can be any length, including 0.

```js
const people = ['Sam', 'Zara', 'Autumn', 'Cadence', 'Gale']
const grades = [91, 83, 100, 87]
const emptyArray = []
```

---

## Array indexes

An _index_ is a number that points to a position in an array. Indexes start at 0 and go to (length - 1), where length is the length of the array.

```js
const people = ['Sam', 'Zara', 'Autumn', 'Cadence', 'Gale']

people[0] // => "Sam"
people[1] // => "Zara"
people[4] // => "Gale"
people[people.length - 1] // => "Gale"
```

---

## Array properties

Arrays have a `.length` property that gives us the length of the array.

```js
const colors = ["red", "purple", "blue", "orange"]
colors.length // => 4
```

[MDN JavaScript Reference: Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

---

## Looping through an array with `for`

We can use a `for` loop to get each index in an array and then use that index to get each item in the array in turn.

```js
for (let i = 0; i < people.length; i++) {
  console.log('Hello, ' + people[i] + '!')
}
```

---

## Using `while` to loop through an array

```js
let i = 0
while (i < people.length) {
  console.log(i, people[i])
  i += 1
}
```

---

## `for...of` loops

For a simpler way to loop over an array and get each item, we can use a `for...of` loop.

```js
for (let person of people) {
  console.log('Hello, ' + person + '!')
}
```

As the loop runs, each member of `people` is assigned to `person` in order. We _do not_ get the index in this case.

---

## Array methods

Arrays have many methods to let us manipulate and interrogate them.

A _method_ is the name for a function that we can access like a property. You need to use parentheses after a method to call it, just like you do with a function.

You'll need to look them up. A lot.

[MDN JavaScript Reference: Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

---

## Adding to and removing from the ends of arrays

Here are some methods that we use all the time with arrays.

```js
const students = ['Sam', 'Val', 'Landry']
students.push('Charlie')
students // => ["Sam", "Val", "Landry", "Charlie"]

students.pop() // => "Charlie"
students // => ["Sam", "Val", "Landry"]

students.unshift('Logan')
students // => ["Logan", "Sam", "Val", "Landry"]

students.shift() // => "Logan"
students // => ["Sam", "Val", "Landry"]
```

---

## Finding things in arrays
### with `indexOf()`

```js
const students = ['Sam', 'Val', 'Landry']

students.indexOf('Val') // => 1
students.indexOf('Landry') // => 2
students.indexOf('Logan') // => -1
```

---

## Removing things from arrays
### with `splice()`

```js
const students = ['Sam', 'Val', 'Landry']
const idx = students.indexOf('Val')
students.splice(idx, 1) // => ["Val"]
students // => ["Sam", "Landry"]
```

---

## Copying arrays

```js
students.slice() // returns a new array
```

A newer syntax for copying arrays uses three dots `...` called the _spread operator_.

```js
let newArray = [...students]
```

---

## Common array actions

Three things we often want to do with arrays are:

- Transform an array (create a new array of the same length with derived values)
- Filter an array
- Get a single value from an array (sum, min, max, etc)

Let's see two techniques for each of these.

---

## Steps in transforming an array

1. Create a new array
2. Loop over the original array
3. For each element of the original array, transform it
4. Push the new transformed element into the new array

---

## Transforming an array, example 1

Get word lengths

```js
const words = ['tapeworm', 'gnarly', 'armoire']
const wordLengths = []

for (let word of words) {
  wordLengths.push(word.length)
}

// wordLengths => [8, 6, 7]
```

---

## Transforming an array, example 2

Is the score a passing grade?

```js
const scores = [91, 54, 78, 39, 81]
const passingGrades = []

for (let score of scores) {
  passingGrades.push(score >= 60)
}

// passingGrades => [true, false, true, false, true]
```

---

## Steps in filtering an array

1. Create a new array
2. Loop through the original array
3. For each element of the original array, test to see if you want to keep it
4. If you want to keep it, push the element into the new array

---

## Filtering an array, example 1

Get only words that have more than six letters.

```js
const words = ['tapeworm', 'gnarly', 'armoire']
const filteredWords = []

for (let word of words) {
  if (word.length > 6) {
    filteredWords.push(word)
  }
}

// filteredWords => ["tapeworm", "armoire"]
```

---

## Filtering an array, example 2

Keep only passing scores.

```js
const scores = [91, 54, 78, 39, 81]
const passingScores = []

for (let score of scores) {
  if (score >= 60) {
    passingScores.push(score)
  }
}

// passingScores => [91, 78, 81]
```

---

## Steps to getting one value from an array

### aka "reducing" an array

1. Find a starting value. This depends on the problem. If you want a sum, start with 0.
2. Loop over your array
3. For each element of the array, compare to the current value. If you need to update the value, do that.

This can be hard to follow!

---

## Reducing an array, example 1

Find the sum of all the numbers in the array.

```js
const scores = [91, 54, 78, 39, 81]
const sum = 0

for (let score of scores) {
  sum += score
}

// sum => 343
```

Here's the example we went over in class, logging each step so you can see what is happening:

```js
for (let score of scores){
console.log("sum is at: ", sum)
console.log("current score is: ", score)
sum += score // the value of sum changes here at this line!
console.log("Now that I've added the score to the sum I have ", sum)
}
```

---

## Reducing an array, example 2

Find the shortest word.

```js
const words = ['tapeworm', 'gnarly', 'armoire']
const shortestWord = null

for (let word of words) {
  if (shortestWord === null || word.length < shortestWord.length)
    shortestWord = word
}

// shortestWord = "gnarly"
```

---

## BUT WAIT!

### JavaScript has built-in Array methods that do all these common transformations



- `.map()`  - _transforms an array into a new array_
- `.filter()` - _keeps items that match a condition, returns a new array_
- `.reduce()` - _produces a single value from an array_

## These methods take functions as arguments.

---

## Two different ways to declare functions with names

In JavaScript, functions are another type of value.

Functions can have names, via the `function` keyword:

```js

function greeting (name) {
  return `Hello, ${name}.`
}

```

...or saved to a variable with `let/const`:

```js
const greeting = function (name) {
return `Hello, ${name}.`
}

```
 ☝️Notice that there is no name after the `function` keyword in this example; the name of the function is the variable name. This is called a _function expression_.

---

## Anonymous functions

Functions can also have no name. When we don't give them a name they are called _anonymous_ functions.

Here's an example of a anonymous function that uses the function keyword. Notice that there's no name after the function keyword and before the parentheses!

```js
function (score) {
  return score > 60
}
```

You might be wondering how we _call_ this function. Good catch!

Anonymous functions are useful when we are using a function as an argument, which we do with `map`, `filter`, and `reduce`.

---

## Transforming an array with `map`

Get word lengths.

```js
const words = ['tapeworm', 'gnarly', 'armoire']
const wordLengths = words.map(function (word) {
  return word.length
})
```

Note that `map` runs the loop for us! The anonymous function it takes as an argument (the _callback_ function) takes the individual elements one at a time as its argument (_`word`_).

`wordLengths` is the new array returned by `map`.

---

## Filtering an array with `filter`

```js
const words = ['tapeworm', 'gnarly', 'armoire']
const filteredWords = words.filter(function (word) {
  return word.length > 6
})

// filteredWords => ["tapeworm", "armoire"]
```

The filtering function should return true or false for each element.

You could think of this as the "keep" method. Elements which return `true` are kept.

---

## Reducing an array with `reduce`

```js
const scores = [91, 54, 78, 39, 81]
const sum = scores.reduce(function (total, score) {
  return total + score
}, 0)

// score => 343
```

---

## The reduce method, in detail

Note that `.reduce()` takes two arguments:

- a function that takes the current reduced value (also called the "accumulator") and the next array element as arguments
- the starting value (this is optional -- if you don't include it, the first array element is used as the accumulator, and the starting value will be the next item in the array)

Here is a demo that might help you visualize what is happening: [http://reduce.surge.sh/](http://reduce.surge.sh/)

---

## Reducing an array, example

```js
const words = ['tapeworm', 'gnarly', 'armoire']
const shortestWord = words.reduce(function (current, word) {
  if (word.length < current.length) {
    return word
  } else {
    return current
  }
})

// shortestWord = "gnarly"
```

We are not providing a starting value here, because we don't need to. It's simpler to use the first word as the value of "current" than to include 'null' as a starting value and then have to handle that case in our function.

---

## Arrow functions

For simple anonymous functions, the _arrow syntax_ is sometimes used. Curly braces are not needed and the return is implicit.

```js
function (score) {
  return score > 60
}

// vs
(score) => score > 60

// or even
score => score > 60
```

---

## Arrow function examples

```js
const words = ['tapeworm', 'gnarly', 'armoire']
const wordLengths = words.map(word => word.length)
const filteredWords = words.filter(word => word.length > 6)

const scores = [91, 54, 78, 39, 81]
const sum = scores.reduce((total, score) => total + score)
```
