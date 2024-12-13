# Challenge #5: 👞 Shoe pairing

#### Level: `🟢 EASY`

## Instructions

`Santa Claus's elves` 🧝🧝‍♂️ have found a bunch of mismatched magic boots in the workshop. Each boot is described by two values:

- type indicates if it's a left boot (I) or a right boot (R).
- size indicates the size of the boot.

Your task is to help the elves pair all the boots of the same size having a left and a right one. To do this, you should return a list of the available sizes after pairing the boots.

**Examples:**

```js
const shoes = [
  { type: "I", size: 38 },
  { type: "R", size: 38 },
  { type: "R", size: 42 },
  { type: "I", size: 41 },
  { type: "I", size: 42 },
];

organizeShoes(shoes);
// [38, 42]

const shoes2 = [
  { type: "I", size: 38 },
  { type: "R", size: 38 },
  { type: "I", size: 38 },
  { type: "I", size: 38 },
  { type: "R", size: 38 },
];
// [38, 38]

const shoes3 = [
  { type: "I", size: 38 },
  { type: "R", size: 36 },
  { type: "R", size: 42 },
  { type: "I", size: 41 },
  { type: "I", size: 42 },
];

organizeShoes(shoes3);
// [42]
```

## Solution (TS)

```ts
type Shoe = {
  type: "I" | "R";
  size: number;
};

function organizeShoes(shoes: Shoe[]): number[] {
  let sol = [];
  const leftShoe = shoes.filter((s) => s.type === "I");
  const rightShoe = shoes.filter((s) => s.type === "R");

  leftShoe.forEach((ls) => {
    const allFinded = rightShoe.filter((rs) => rs.size === ls.size);
    if (allFinded.length > 0) {
      sol.push(ls.size);
      const idx = rightShoe.indexOf(allFinded[0]);
      rightShoe.splice(idx, 1);
    }
  });
  return sol;
}
```
