# Coding Tasks

**Note**

Where applicable, try to do the coding tasks with [ping pong pair programming](http://wiki.c2.com/?PairProgrammingPingPongPattern).

For example, in your pairs, person A could do task 2, observe that the test fails because task 3 has not been completed.

Person B then implements the code for task 3.

You then re-run the test and find that it passes.

Then Person B writes the test and code for task 4.

Person A writes the code and implements the function for task 5 and so on and so on.

## 1) Run the tests for `catalogueService.checkBook`

There are currently tests for just one function - if you run the test `npm run test` you'll notice the tests are failing.

## 2) Implement the `catalogueService.checkBook` function

Open the `app/catalogue_service.js` file and implement the `checkBook` function so that the tests now pass.

**Hint**

The code in the test itself does NOT need changing

## 3) Add more tests?

Are there any more tests you want to add to the `catalogueService.checkBook` function? Can you think of any edge cases? For example, what if the function is called with a book title in lowercase?

```javascript
catalogueService.checkBook("great expectations");
```

In this case, should the function ignore case and return `true`? Think about what behaviour you'd like to see from your function.

Write at least 1 further test, run the test and ensure it passes.

## 4) _While_ you're at it...

Before you move onto the next function, if you used a **for loop** in the `checkBook` function, can you change it to a **while** loop?

Or vice versa, if you started off with a **while loop** can you change it for a **for loop**?

The tests should still pass after this **refactor**.

## 5) Write a test for `countBooksByKeyword`

This function should return a count (Number) of how many book titles match a given keyword. For example, if it is called with the keyword "assassin" then it should return the number of books in the catalogue with this keyword.

```javascript
catalogueService.countBooksByKeyword("assassin"); // returns 3
catalogueService.countBooksByKeyword("normal"); // returns 2
```

Run the test and see that it fails

## 6) Update your `countBooksByKeyword` function

Your `countBooksByKeyword` function should now be updated to pass the test you just wrote.

## 7) More tests

Think about more input you can test. For example, what if the keyword is not found? Ensure you have a test that tests that `0` is returned in this scenario.

```javascript
catalogueService.countBooksByKeyword("pineapple"); // returns 0
```

What about other edge cases?

What if someone calls the function with a number? Or a boolean? Or some other value that doesn't make sense?

Should the function attempt to treat the number as a string, or not? This is up to you - discuss with your pair how you think the function should behave and any problems you foresee.

E.g.:

```javascript
catalogueService.countBooksByKeyword(2666);
catalogueService.countBooksByKeyword(true);
catalogueService.countBooksByKeyword([1, 2, 3]);
```

## 8) Write a test for `getBooksByAuthor`

The catalogueService should be able to provide a list of books by a given author.

For example:

```javascript
catalogueService.getBooksByAuthor("Charles Dickens");
```

Should return:

```javascript
["A Tale of Two Cities", "Oliver Twist", "Great Expectations"];
```

Note that the author's name is not included in the result!

Write a test for this function. It should fail at the moment.

**NB** When testing a return value of an **array** or **object** (complex data types) we need to use the `.toEqual()` method from Jest instead of `.toBe()`. So your test may look like:

```javascript
expect(catalogueService.getBooksByAuthor("Charles Dickens")).toEqual([
  "A Tale of Two Cities",
  "Oliver Twist",
  "Great Expectations"
]);
```

## 9) Update your `getBooksByAuthor` function

Update the `getBooksByAuthor` function so that the previous test passes.

## 10) More tests

Again, can you write some more tests for the `getBooksByAuthor` function? What if there are no books found, for example? Ensure that the function returns an empty array `[]`.

How about if the author's name is simply provided as `"Charles"`? You would expect books by both Charles Darwin and Charles Dickens to be returned.

## 11) Write a test for `getStockCount`

The Catalogue service should be able to return the number of items that are in stock of a given title. In the list of books, the number in brackets indicates the number of that title currently in stock.

For example:

```javascript
catalogueService.getStockCount("Between the Assassinations"); // Returns 9
catalogueService.getStockCount("A Tale of Two Cities"); // Returns 3
```

Write a test to check this functionality. The test should fail at the moment.

## 12) Update your `getStockCount` function

Implement the code to ensure the above test works.

## 13) More tests

As usual, write further tests to check extra cases. For example, check that `0` is returned when the book's stock count is 0.

What if a book is not listed? Decide with your pair how you want the function to behave.

```javascript
catalogueService.getStockCount("The Great Gatsby"); // Should return 0? Or "Not in our catalogue" ?
```

## 14) Write a test for `stockReview`

The Catalogue service should also be able to give you a rough overview of how well stocked your collection is in a specific title. In the list of books, the number in brackets indicates the number of that title currently in stock.

| Quantity of Titles |              |
| ------------------ | ------------ |
| 0                  | Not in Stock |
| 1-5                | Low Stock    |
| 6 - 10             | Medium Stock |
| 11+                | High Stock   |

Write an initial test to check what happens when the `stockReview` function is called with a book that is not in stock.

```javascript
catalogueService.stockReview("Dracula"); // returns "Not in Stock"
```

## 15) Begin to implement the `stockReview` function

Write the code to ensure that the test you just wrote now passes.

## 16) Test the other cases

Write tests and implement the code for the other 4 cases.

## 17) Switch it up

If you used `if` statements in your `stockReview` function, change them to a `switch` statement.

If you used a `switch` statement, change it to `if` statements.

Ensure the tests still pass after you have made this **refactor**.

Which do you think was a better way to implement the function? Why?

# Written questions

The following questions are intended to be answered with written answers (no coding required) and should re-enforce some of the learning you have completed.

1. In what data type have we chosen to represent a book?

2. Is this the best data type, do you think? Could we have chosen a more appropriate data type? Why?

3. Take a read of the Jest Documentation about [Matchers](https://jestjs.io/docs/en/using-matchers) such as `toBe` and `toEqual`. What other matchers might come in useful? Check the tests you have written and make a list of alternative matchers which you might have been able to use.

4. What data types are considered "complex" data types?

5. What data types are considered "primitive" data types?

6. In JavaScript it is possible to use `==` ("double equals") or `===` ("triple equals") to compare two values. What is the difference and why do we prefer triple equals?
