
Using the correct array methods could convey a clearer intent, make code more readable and avoid performing unneccessary operations (and hence a performance gain).
It is encouraged to strive to use the appropriate methods whenever possible.

Below are some of the commonly-used array methods that you should master:

**array.find**

array.find(`predicate`) method returns the first array item that passes the `predicate` function.

`find` returns the element as soon as the first element passes the predicate, and skips evaluating the rest of the elements;
`filter` evaluates all elements in the array, which is unneccessary if we are interested in only the first element.
```
arr.find(a => a === x); // good

arr.filter(a => a === x)[0]; // bad
```

**array.includes**

array.includes(`itemToSearch`) returns a boolean whether array contains `itemToSearch`.

`includes` returns `true` as soon as `itemToSearch` is found, and skips evaluating the rest of the elements.

```
arr.includes(x); // good

arr.find(a => a === x) !== undefined; // bad
arr.filter(a => a === x)[0] !== undefined; // bad
arr.filter(a => a === x).length; // bad
```

**array.some**

array.some(`predicate`) returns a boolean whether array contains element that passes the `predicate` function.

`some` returns `true` as soon as the first element passes the predicate, and skips evaluating the rest of the elements.

```
arr.some(isOdd); // good

arr.find(isOdd) !== undefined; // bad
arr.filter(isOdd)[0] !== undefined; // bad
!!arr.filter(isOdd).length; // bad
```

**array.every**

array.every(`predicate`) returns a boolean whether all elements in the array passes the `predicate` function.

`every` returns `false` as soon as one element fails the predicate, and skips evaluating the rest of the elements.

```
arr.every(isOdd); // good

!arr.some(!isOdd); // bad
arr.find(!isOdd) !== undefined // bad
arr.filter(isOdd).length === arr.length // bad
!!arr.filter(!isOdd).length // bad
```

**Appendix**

The following expressions are all equivalent. Option 1 or 2 is preferred.
```
1. arr.filter(isOdd); // preferred

2. arr.filter(num => isOdd(num)); // preferred

3. arr.filter(num => { 
  return isOdd(num);
});

4. arr.filter(function(num) { 
  return isOdd(num);
});
```
