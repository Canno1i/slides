# map, filter, reduce

### Array methods for functional programming

## map

- modifies each entry in an array via a function
- returns a new array

```js
let myNumbers = [2, 10, 23];

let triple = n => 3 * n;

let newNumbers = myNumbers.map(triple);
// [6, 30, 69]
```

## filter

- only keeps specific entries in an array
- uses a function to check entries for a specific criterion
- returns a new array

```js
let myNumbers = [2, 10, 23];

let isEven = n => n % 2 === 0;

let newNumbers = myNumbers.filter(isEven);
// [2, 10]
```

## reduce

- Verarbeitet die Einträge in einem Array zu einem einzelnen Wert
- Verwendet eine Funktion, die aus zwei bestehenden Werten einen resultierenden Wert erstellt - diese Funktion wird wiederholt aufgerufen

## reduce - Beispiel

```js
let transactions = [
  { amount: -56, title: 'groceries' },
  { amount: +1020, title: 'salary' },
  { amount: -13, title: 'dinner' },
  { amount: -96, title: 'electricity' },
];
let initialBalance = 317;

let currentBalance = transactions.reduce(
  (aggregator, transaction) =>
    aggregator + transaction.amount
);

// 317 -> 261 -> 1281 -> 1268 -> 1172
```