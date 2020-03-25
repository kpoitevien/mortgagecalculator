# Read this whole document before doing any work!

What's cooler than an online tip calculator?
An online mortgage calculator!

The basic concept is of course the same:
  * Ask the user a series of questions
  * Do some math once the user submits their answers
  * Show a result on the screen

The math is just a __teensy weensy__ more complicated.  After reading [this article](https://www.wikihow.com/Calculate-Mortgage-Payments#Calculating_Mortgage_Payments_with_an_Equation), I wrote a function for you below that you can use instead of dealing with the math yourself.

```js
function calculateMonthlyPayment(principal, annualRate, numberOfYears){
  const monthlyRate = annualRate / 12 / 100
  const numberOfPayments = numberOfYears * 12
  const numerator = monthlyRate * (1 + monthlyRate) ** numberOfPayments
  const denominator = (1 + monthlyRate) ** numberOfPayments - 1
  return principal * (numerator / denominator)
}
```

You can see that the function `return`s the monthly mortgage payment, which can then be stored in a constant.

```js
const principal = 300000
const annualRate = 4.125
const numberOfYears = 30

const payment = calculateMonthlyPayment(principal, annualRate, numberOfYears)

console.log(payment) // 1453.949197494022
```

# The Big Idea

Create a program that asks the user three questions:
  * What is the principal on the loan?
  * What is the annual rate of the loan?
  * What is the term (in years) of the loan?

And then shows the user the monthly payment for the loan.

You can do this work __either__ in the `mortgage.js` __or__ inside the `mortgage.html` file inside this repository.  We have started off each file for you.  __BONUS POINTS__ if you can complete both tasks in the alotted time.

## Setup

* `git clone` this repository
* `cd` into the `mortgage_calculator` folder
* Make an `enhancement` issue on this repository called "mortgage calculator" and assign it to yourself.
* Checkout a unique branch for your work with the naming convention `enhancement-(issue-number)-(your-name)-mortgage-calculator`.
* `yarn` -- this will make sure you have `readline-sync` correctly installed for this project.

## Instructions (mortgage.js)

* Use the `readline-sync` library to ask the user for the the principal, rate, and term of the loan.
* Convert their answers into numbers.  If the answers are not numbers, or are negative, log an error message to the console and ask again.
* Calculate the monthly payment using the function above, and log it to the console.

Your program should look something like this when finished:
![node screenshot](node_screenshot.png)

## Instructions (mortgage.html)

* Create number inputs for the principal and rate.  Give them a `min` attribute that will prevent negative numbers from being submitted.
* Create a select for the term of the mortgage.  Show the user options like "15 year fixed" or "30 year fixed" but the `value` attribute on the options should be numeric: "15" or "30" in this case.
* Create a button to submit the form.
* Inside the answer div, place an h2 tag that will show the correct answer.  Place the actual answer in a span with a unique id so you can change its `textContent` with JavaScript.
* Query the dom to store each input or select in a `const`.
* Write a function called `handleFormSubmit`.  This function needs to accept the `submit` event as a parameter so you can immediately call `preventDefault()` on it.
* Inside the function, take the `value` of each input or select and convert each to a number.
* Pass these values into the `calculateMonthlyPayment` function and store the result in a `const`.
* Update the answer's `textContent` and remove the `hidden` class from the answer div.

Your program should look something like this when finished:

![browser screenshot](browser_screenshot.png)

## Submitting

* Save all files.
* `git add .` and `git commit -m "mortage calculator"`.
* `git push -u origin your-branch-name`
* Open a pull request that `closes` your issue number and request my review.





