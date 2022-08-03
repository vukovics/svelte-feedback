<script lang="ts">
  import svelteLogo from './assets/svelte.svg';
  import firebaseLogo from './assets/firestore.svg';
  import FeedbackButton from './lib/components/FeedbackButton.svelte';
  import FeedbackListButton from './lib/components/FeedbackListButton.svelte';
</script>

<main>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite Logo" />
    </a>
    <a href="https://svelte.dev" target="_blank">
      <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
    </a>
    <a href="https://firebase.google.com/" target="_blank">
      <img src={firebaseLogo} class="logo firebase" alt="Firebase Logo" />
    </a>
  </div>

  <h1>Vite + Svelte + Firebase</h1>
  <FeedbackListButton />
  <FeedbackButton />
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
</style>
