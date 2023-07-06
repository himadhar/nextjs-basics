---
title: 'Unit Testing using TypeScript (TS)'
date: '2017-11-11'
---

Unit Testing using TypeScript (TS)

## Introduction

![](/images/blogs/js-basics.jpeg)

I have been through multiple websites to find a solution to handle TypeScript unit testing and seems like using the Karma-Jasmine combination is a good start. With this post, I intend to summarize it and hope it helps you while doing so.

Below are a set of configurations you need to have to proceed.

## Prerequisites
Before getting started, make sure you have the following prerequisites installed:
- [Node.js](https://nodejs.org/en/) and npm (Node Package Manager)

## Steps for Setting up Unit Testing with Karma and Jasmine

1. **Initialize the Project**: Start by setting up a new TypeScript project or using an existing one. Open your project directory in the command line and run the following command to initialize a new `package.json` file:

```
npm init -y
```

2. **Install Dependencies**: Install the necessary dependencies by running the following commands:
```
npm install karma karma-cli karma-jasmine jasmine-core karma-chrome-launcher karma-typescript
```

3. **Configure Karma**: Create a `karma.conf.js` file in your project directory to configure Karma. Add the following content to the file:

```
javascript
module.exports = function (config) {
  config.set({
    frameworks: ['jasmine', 'karma-typescript'],
    files: [
      'src/**/*.ts',
      'test/**/*.spec.ts'
    ],
    preprocessors: {
      '**/*.ts': 'karma-typescript'
    },
    reporters: ['progress', 'karma-typescript'],
    browsers: ['Chrome'],
    singleRun: true,
    concurrency: Infinity
  });
};
```

Create Unit Tests: Create your unit test files with the .spec.ts extension inside a test directory. Write your test cases using the Jasmine syntax.

Run the Tests: Execute the following command to run your unit tests:

```
karma start
```

Karma will launch a browser (Chrome in this case) and run your tests, displaying the results in the command line.

## Example

### code.ts

```
function subtract(a: number, b: number): number {
  return a - b;
}
```
### test.ts
```
describe('subtract method', () => {
  it('subtracts 2 numbers', () => {
    expect(subtract(2, 4)).toBe(-3);
  });
  it('subtracts 2 numbers', () => {
    expect(subtract(2, 4)).toBe(-2);
  });
});
```

## Conclusion
By following these steps, you can set up unit testing for your TypeScript code using Karma and Jasmine. Writing unit tests helps ensure the correctness and reliability of your code, leading to more robust software development. Start writing tests for your TypeScript projects and enjoy the benefits of a well-tested codebase.


<h6 style="text-align: right">
- Himadhar
</h6>