# Svelte + TS + Vite + Firebase

This template should help get you started developing with Svelte and TypeScript in Vite.

# Install
```
npm i feedbacky-svelte-firebase
```
## Usage

```javascript
var feedback = require('feedback');

// In your svelte app add these 2 components
feedback.color = false;

//
feeback.write('message') // same as process.stdout
feedback.writeln('message') // same as write() but begins with a new line
feedback.info('message') // same as console.log()
feedback.success('message') // same as console.log(), but adds "Success: " to beginning
feedback.warn('message') // same as console.log(), but adds "Warning: " to beginning
feedback.error('message') // same as console.log() but add "Error: " to beginning
```

# Run the app locally
- npm install
- npm run dev
