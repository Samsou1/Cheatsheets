# JS

## Fetch

```
const url = 'somerandomapi.com/items'
fetch(url)
      .then(response => response.json())
      .then(json => console.log(json))
      .catch(error => console.log(error));
```

## Map

```
var newTable = arr.map(callback [, thisArg])
```

Example:
```
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
```
What arguments you can use:
```
const map2 = array 2.map((currentValue, index, initialArray) => somefunction())
```
Map doesn't change the previous array.

## Filter

```
var nouveauTableau = arr.filter(callback, thisArg);
```

Example
```
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]

```

What arguments you can use:
```
const filter = array 2.filter((currentValue, index, initialArray) => somefunction())
```
Filter doesn't change the previous array.

## Reduce

```
arr.reduce(callback, initialValue)
```

Example
```
const array1 = [1, 2, 3, 4];

// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (previousValue, currentValue) => previousValue + currentValue,
  initialValue
);

console.log(sumWithInitial);
// expected output: 10

```

What arguments you can use:
```
const reduce = array 2.reduce((accumulator, currentValue, index, initialArray) => { someFunction
  }, initialValue)
```
Reduce doesn't change the previous array.