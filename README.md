# test-generator

A library to generate test files based on comments

I am trying to validate an idea here. Because of adhoc and rapid development, there are time where developer is not able
to write test and automate it. But developers tends to write comments in there just to remember the context of complex codes.

**What if writting comments in specific structure can generate the test files for you 🤔 ?**
It would be great if we can achieve this. Initially lets start with unit testing!

Lets define the structure for testing comments 🚀

## Thoughts

> Note: Initially make it work for node simple functions

- We will be using [Jest](https://jestjs.io/) as testing framework
- Use same jargon as of Jest
- Each file comments will result in a new test file
  - [Open Question] How imports will work?
- Use ast to get comment blocks and find the Jest word patterns
- Generate the `[file].test.js` in `__test__` folder
  - extract the tests
  - import \* from the file where tests are written

### Example Input

- `sum.js`

```js
/*
 expect(sum(1, 2)).toBe(3);
*/

export function sum(a, b) {
  return a + b;
}
```

### Example output

- `__test__/sum.test.js`

```js
import * as ModuleName from ../sum

test('test 1', () => {
  expect(ModuleName.sum(1, 2)).toBe(3);
});
```
