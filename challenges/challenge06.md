# Challenge #6: 📦 Is the gift inside the box?

#### Level: `🟠 MEDIUM`

## Instructions

We have already wrapped hundreds of presents 🎁… but an elf forgot to check if the present, represented by an asterisk \*, is inside the box.

The box has a present (\*) and counts as "inside the box" if:

- It is completely surrounded by # on the box's edges.
- The \* is not on the box's edges.

Keep in mind that the _ can be inside, outside, or may not even be there. We must return true if the _ is inside the box and false otherwise.

**Examples:**

```js
inBox(["###", "#*#", "###"]); // ➞ true

inBox(["####", "#* #", "#  #", "####"]); // ➞ true

inBox(["*####", "#   #", "#  #*", "####"]); // ➞ false

inBox(["#####", "#   #", "#   #", "#   #", "#####"]); // ➞ false
```

## Solution (TS)

```ts
function inBox(box: string[]): boolean {
  const noBorderBox = box.slice(1, box.length - 1);
  let newBox: string[] = [];
  for (let i = 0; i < noBorderBox.length; i++) {
    const removedBorders = noBorderBox[i].slice(1, noBorderBox[i].length - 1);
    newBox.push(removedBorders);
  }
  return newBox.some((l) => l.includes("*"));
}
```
