---
title: Euclidean distance
tags: math,algorithm
expertise: intermediate
author: chalarangelo
cover: blog_images/ancient-greek-building.jpg
firstSeen: 2020-12-28T13:41:19+02:00
lastUpdated: 2020-12-28T13:41:19+02:00
---

Calculates the distance between two points in any number of dimensions.

- Use `Object.keys()` and `Array.prototype.map()` to map each coordinate to its difference between the two points.
- Use `Math.hypot()` to calculate the Euclidean distance between the two points.

```js
const euclideanDistance = (a, b) =>
  Math.hypot(...Object.keys(a).map(k => b[k] - a[k]));
```

```js
euclideanDistance([1, 1], [2, 3]); // ~2.2361
euclideanDistance([1, 1, 1], [2, 3, 2]); // ~2.4495
```

But isn't this essentially the same as the following?

```javascript
const dist = ((a, b) => {
    return Math.hypot(...b.map((k, i) => b[i] - a[i]));
})
```

```javascript
Object.keys([1, 2, 1, 1, 2]); // [0, 1, 2, 3, 4] 
dist([1, 1, 1], [2, 3, 2]) === euclideanDistance([1, 1, 1], [2, 3, 2]); // true
dist([1, 1], [2, 3]) === euclideanDistance([1, 1], [2, 3]); // true
```
Since `Object.keys` just returns the index of the array item, and it's already provided via `Array.prototype.map`?
