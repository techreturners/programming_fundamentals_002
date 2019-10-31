# Coding Tasks

**Note**

Where applicable, try to do the coding tasks with [ping pong pair programming](http://wiki.c2.com/?PairProgrammingPingPongPattern).

For example, in your pairs, person A could do task 2, observe that the test fails because task 3 has not been completed.

Person B then implements the code for task 3.

You then re-run the test and find that it passes.

Then Person B writes the test and code for task 4.

Person A writes the code and implements the function for task 5 and so on and so on.

## 1) Run the tests for `catalogueService.countBooks`

There are currently tests for just one function - if you run the test `npm run test` you'll notice the tests are failing.

## 2) Implement the `catalogueService.countBooks` function

Open the `app/catalogue_service.js` file and implement the `countBooks` function so that the tests now pass.

**Hint**

The code in the test itself does NOT need changing

## 3) Write a test for `checkBook`

The function should return `true` if the book in question is available in the array and `false` if not. The function will receive a string as an argument.

You should organise your tests like this:

```javascript
describe("catalogueService", () => {
  describe("catalogueService.countBooks", () => {
    test("returns the number of books in the list", () => {
      expect(catalogueService.countBooks()).toBe(20);
    });
  });

  describe("catalogueService.checkBook", () => {
    test("returns true if the book exists in the list", () => {
      expect(catalogueService.checkBook("Dracula by Bram Stoker")).toBe(true);
    });
  });
});
```

## 4) Implement the `catalogueService.checkBook` function

In the `app/catalogue_service.js` file, implement the `checkBook` function so that the tests now pass.

## 5) Another test

What about if the book is not in stock? We need to test that the function also returns the right value (`false`) in this case - which means another test!

Update your tests to add another:

```javascript
describe("catalogueService", () => {
  describe("catalogueService.countBooks", () => {
    test("returns the number of books in the list", () => {
      expect(catalogueService.countBooks()).toBe(20);
    });
  });

  describe("catalogueService.checkBook", () => {
    test("returns true if the book exists in the list", () => {
      expect(catalogueService.checkBook("Dracula by Bram Stoker")).toBe(true);
    });

    test("returns false if the book exists in the list", () => {
      expect(catalogueService.checkBook("Moths by Pamela Mothman")).toBe(false);
    });
  });
});
```

## 6) Ensure this test passes

Run your tests, perhaps it already passes? If not, you'll need to go back to `app/catalogue_service.js` and take another look at the `checkBook` function to ensure it returns `false` if the item is not available.

## 7) Write a test for `countBooksByFirstLetter`

This function will receive a letter, such as "N", and return a number of how many books begin with this letter.

Begin by adding another `describe` block below the previous one and writing a test for this function. For example:

```javascript
describe("catalogueService.countBooksByFirstLetter", () => {
  test("returns the number of books beginning with the given letter", () => {
    expect(catalogueService.countBooksByFirstLetter("W")).toBe(2);
  });
});
```

## 8) Implement the `catalogueService.countBooksByFirstLetter` function

In the `app/catalogue_service.js` file, implement the `countBooksByFirstLetter` function so that the test now passes.

## 9) What if there are no books?

Add another test that checks that 0 is returned if no books begin with the given letter.

```javascript
describe("catalogueService.countBooksByFirstLetter", () => {
  test("returns the number of books beginning with the given letter", () => {
    expect(catalogueService.countBooksByFirstLetter("W")).toBe(2);
  });

  test("returns 0 if no books begin with the given letter", () => {
    expect(catalogueService.countBooksByFirstLetter("X")).toBe(0);
  });
});
```

Ensure this test passes and if it doesn't, you'll want to take a look at your function!

## 10) Write a test for `countBooksByKeyword`

This function should return a count (Number) of how many book titles match a given keyword. For example, if it is called with the keyword "assassin" then it should return the number of books in the catalogue with this keyword.

```javascript
catalogueService.countBooksByKeyword("assassin"); // returns 3
catalogueService.countBooksByKeyword("normal"); // returns 2
```

Run the test and see that it fails

## 11) Update your `countBooksByKeyword` function

Your `countBooksByKeyword` function should now be updated to pass the test you just wrote.

## 12) More tests

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

## 13) Write a test for `getBooksByAuthor`

The catalogueService should be able to provide a list of books by a given author.

For example:

```javascript
catalogueService.getBooksByAuthor("Charles Dickens");
```

Should return:

```javascript
[
  "A Tale of Two Cities by Charles Dickens",
  "Oliver Twist by Charles Dickens",
  "Great Expectations by Charles Dickens"
];
```

Write a test for this function. It should fail at the moment.

**NB** When testing a return value of an **array** or **object** (complex data types) we need to use the `.toEqual()` method from Jest instead of `.toBe()`. So your test may look like:

```javascript
expect(catalogueService.getBooksByAuthor("Charles Dickens")).toEqual([
  "A Tale of Two Cities by Charles Dickens",
  "Oliver Twist by Charles Dickens",
  "Great Expectations by Charles Dickens"
]);
```

## 14) Update your `getBooksByAuthor` function

Update the `getBooksByAuthor` function so that the previous test passes.

## 15) More tests

Again, can you write some more tests for the `getBooksByAuthor` function? What if there are no books found, for example? Ensure that the function returns an empty array `[]`.

How about if the author's name is simply provided as `"Charles"`? You would expect books by both Charles Darwin and Charles Dickens to be returned.

# Written questions

The following questions are intended to be answered with written answers (no coding required) and should re-enforce some of the learning you have completed.

1. In what data type have we chosen to represent a book?

2. Is this the best data type, do you think? Could we have chosen a more appropriate data type? Why?

3. Take a read of the Jest Documentation about [Matchers](https://jestjs.io/docs/en/using-matchers) such as `toBe` and `toEqual`. What other matchers might come in useful? Check the tests you have written and make a list of alternative matchers which you might have been able to use.

4. What data types are considered "complex" data types?

5. What data types are considered "primitive" data types?

6. In JavaScript it is possible to use `==` ("double equals") or `===` ("triple equals") to compare two values. What is the difference and why do we prefer triple equals?
