# Simple Express Snippets

The essential collection of Express Snippets and commands.

## Features

Only what you need and nothing more.

Simply, simple Express snippets.

These snippets were selected carefully from my own day-to-day Express use. Not
everything in Express is included here. This is a hand selected set of snippets
that work the way that you would expect, not just a copy of the documentation.

## Snippets

| Snippet    | Renders                         |
| ---------- | ------------------------------- |
| `ess`      | Express simple server Setup     |
| `eue`      | Express URL encoded             |
| `ejson`    | Express set to use json         |
| `estatic`  | Express set the static folder   |
| `esrouter` | Create a simple router object   |
| `ergr`     | A router based get route        |
| `erpr`     | A router based post route       |
| `esgr`     | A simple get route for Express  |
| `espr`     | A simple post route for Express |

## Full Expansions

### ess - Express simple server Setup

```javascript
const express = require("express");
// In typescript
// import express from 'express';

const app = express();

app.listen(3000, () => {
  console.log(`Server is Listening on 3000`);
});
```

### eue - Express URL encoded

```javascript
app.use(express.urlencoded({ extended: false }));
```

### ejson - Express set to use json

```javascript
app.use(express.json());
```

### estatic - Express set the static folder

```javascript
app.use(express.static("public"));
```

### esrouter - Create a simple router object

```javascript
const express = require("express");
// In typescript
// import express from 'express';
const router = express.Router();

module.exports = router;
// In typescript
// export default router;
```

### ergr - A router based get route

```javascript
router.get("", (request, response) => {});
```

### erpr - A router based post route

```javascript
router.post("", (request, response) => {});
```

### espr - A simple based get route

```javascript
app.get("", (request, response) => {});
```

### espr - A simple based post route

```javascript
app.post("", (request, response) => {});
```

## Thank You! ❤️

Special thanks to the following individuals who have helped with this project in
some way.

- [@raxraj](https://twitter.com/raxrajtwit)
- [@anxxica](https://instagram.com/anxxica)
