<script lang="ts">
  import Modal from './Modal.svelte';
  import { slide } from 'svelte/transition';

  let showModal = false;
  let feedbackSent = false;
  let isDisabled = false;

  function onSubmit(e) {
    isDisabled = true;
    const formData = new FormData(e.target);

    let data = {};
    for (let field of formData) {
      const [key, value] = field;
      data[key] = value;
    }

    fetch(
      `https://us-central1-feedbacky-402af.cloudfunctions.net/addFeedback?feedback=${data.feedback}&email=${data.email}22&user=${location.hostname}`
    )
      .then((response) => response.json())
      .then(() => {
        feedbackSent = true;
        setTimeout(() => {
          feedbackSent = false;
          isDisabled = false;
        }, 2000);
      })
      .catch((error) => {
        console.log(error);
        return [];
      });
  }
</script>

<button class="card" on:click={() => (showModal = true)}>Feedback</button>

{#if showModal}
  <Modal on:close={() => (showModal = false)}>
    <h2 style="color:black" slot="header">Send your feedback</h2>
    <form
      in:slide
      style="color:black; display: inline-block;"
      on:submit|preventDefault={onSubmit}
    >
      <div>
        <label for="name">Email</label>
        <input id="name" type="email" name="email" required />
      </div>
      <div>
        <label for="feedback">Feedback</label>
        <textarea
          type="text"
          id="feedback"
          name="feedback"
          maxlength="2000"
          required
        />
      </div>
      <button disabled={isDisabled} style="width:100%" type="submit"
        >Submit</button
      >
    </form>
    {#if feedbackSent}
      <h1 in:slide style="color:green">Feedback sent!</h1>
    {/if}
  </Modal>
{/if}

<style>
  * {
    box-sizing: border-box;
  }

  form {
    display: flex;
    flex-direction: column;
    width: 300px;
  }

  form > div {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }

  form > div + * {
    margin-top: 10px;
  }

  .card {
    position: absolute;
    bottom: 0;
    right: 0;
    z-index: 999999;
  }
</style>
