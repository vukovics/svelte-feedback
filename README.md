# Svelte + TS + Vite + Firebase

Here is [DEMO](https://superb-croquembouche-e621b4.netlify.app/)

# Install

```
npm i feedbacky-svelte-firebase
```

## Usage

```javascript
// Import components from feedbacky-svelte-firebase
<script lang="ts">
  import { FeedbackButton, FeedbackListButton } from 'feedbacky-svelte-firebase';
</script>

// add components to html
<main>
  <FeedbackButton />
  <FeedbackListButton />
<main>
```

## Usage in pure html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite + Svelte + TS + Firebase</title>
    <script type="module" crossorigin src="/assets/index.9b8548c2.js"></script>
    <link rel="stylesheet" href="/assets/index.bdd2d982.css" />
  </head>
  <body>
    <div id="app"></div>
  </body>
</html>
```

# Run the app locally

- npm install
- npm run dev
- npm run build
