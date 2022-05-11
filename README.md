# testing-introduction
First steps to learn about testing with javascript

## Content
1. Goals of testing
2. Manual Testing
3. Unit testing
4. End 2 End Testing

## 1. Goals of Testing
- **Definition**: 
  - (1) Every algorithm has a defined input and unique output. The goal of testing is that the expected output matches the actual one.  

  - (2) Notice, that you can expect more than the output (i.e. functional test), but also everything you expect from the process (i.e. quality) like expected speed or coding standards.  

  - (3) If the expected outcome matches the actual one, the test is ***verified*** - the result is *true*, else it is *false*.  

- In computer science, you deal with unambigous states which all have to lead to a predictable outcome.  

- Even if you use unpredictable random algorithms, your goal is always to be able to handle the data to process it to information and not produce chaos.

- Today and in the future, the amount of data and complexity exponentially increases. The urge to use well defined test strategies early in production helps to narrow down problems, which can occur in every system like air planes or medical devices.

- Definition of ERROR: 
  - (1) The difference between the value which has been computed and the correct value.
  - (2) An error could result in failure or in a deviation from the intended performance or behavior. *(EN 50218, CENELEC 2011)*

## 2. Manual Testing
- One person in the role of a tester follows a written *test plan*, that leads her/him through a set of *test cases*  

- *exploratory testing* involves simultaneous learning, test design and test execution  

- *Static testing* includes verifying requirements, syntax of code and any other activities that do not include actually running the code of the program, which is *dynamic testing*  

- In *white-box testing* the tester is concerned with the execution of the statements through the source code.  
In *black-box testing* the software is run to check for the defects and is less concerned with how the processing of the input is done. Black-box testers do not have access to the source code.  
*Grey-box testing* is concerned with running the software while having an understanding of the source code and algorithms.

## 3. Unit Testing
- Definition:
  - (1) is a (typically) automatic software testing method
  - (2) the smallest part of the software, called unit, is tested, e.g. a function.  

- A unit test provides a strict, written contract that the piece of code must satisfy.  

- In Test Driven Development, where the test is written first before the production code, the test fails at first, but gets "green", as soon as the code is written correctly.  

- Automated tests can be rerun against the code to ensure that the code works as expected (*regression testing*).

### Javscript Testing Framework "Jest"
- There are many testing libaries out there for any kind of programming language. Facebook developed jest, which has become very popular.  

```
npm init
npm install --save-dev jest
```

- Jest looks for *.test.js, or change the pattern in a jest.config.js  

- Next, look at sum.js and sum.test.js in ```jest/```:

---

You've found these functions:

```javascript
test('Description', () => {
})
```

Every test is enclosed in a code block to run the test. A description is added here to identify the test.

```javascript
expect(received).toBe(expected)
```

This is a **matcher**, it will verify, if the expected value "matches" the received one in the way of the method ".toBe). There are other methods, like ".toBeGreaterThan".

Notice, that our tested function is called inside expected. So the *result* of sum() wil be used to compare it with *.toBe(3)*.

Now run in ```jest/```:
```
npm install
npm test
```

---

- In reality, the tested "functions" might not be as simply as sum(), although it might be a goal to work with functions in a way that unit testing is possible. @see *functional programming*.  

- You might use ***procedures*** in your code, where you query the database or you use variables from outer function scope. These values must be simulated, while you have a close look at your current function scope.

- You even can test React JSX Code with unit tests, as this code is returned by a function and therefore can be expected.

## 4. End 2 End Testing
- **Definition**: During End 2 End Tests, the whole application is running tested in a complete round-trip from frontend to backend to frontend.

---
```shell
cd ..
cd playwright-testing
npm install
# install supported browsers
npm test
```

- Have a look at the exmaple.spec.mjs. This file looks similar to the jest sum.test.js.
  - 1. At first, the website playwright.dev is opened.
  - 2. Then a title is found
  - 3. It checked if the title matches "Playwright".  

- A test typically has three phases:
  - 1. Arrange: A test environment is built up.
  - 2. Act: An action is proceeded.
  - 3. Assert: An assertion is made.

