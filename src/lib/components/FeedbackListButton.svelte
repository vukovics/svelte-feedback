<script lang="ts">
  import Modal from './Modal.svelte';

  let showModal = false;
  let feedbacks = [];
  let loader = false;

  function getFeedbaks() {
    loader = true;
    fetch(
      `https://us-central1-feedbacky-402af.cloudfunctions.net/getFeedback?user=${location.hostname}`
    )
      .then((response) => response.json())
      .then((response) => {
        showModal = false;
        feedbacks = response;
        showModal = true;
        loader = false;
      })
      .catch((error) => {
        console.log(error);
        return [];
      });
  }
</script>

<button class="card-list" on:click={() => getFeedbaks()}>Feedback List</button>

{#if loader}
  Loading ...
{/if}

{#if showModal}
  <Modal on:close={() => (showModal = false)}>
    <table>
      <caption>Feedbacks</caption>
      <thead>
        <tr>
          <th scope="col">email</th>
          <th scope="col">Feedback</th>
        </tr>
      </thead>
      <tbody>
        {#each feedbacks as fedback}
          <tr>
            <td data-label="Account">{fedback.email}</td>
            <td title={fedback.feedback} data-label="Due Date"
              >{fedback.feedback}</td
            >
          </tr>
        {/each}
      </tbody>
    </table>
  </Modal>
{/if}

<style>
  * {
    box-sizing: border-box;
  }
  .card-list {
    position: absolute;
    top: 0;
    right: 0;
    z-index: 999999;
  }

  table {
    color: black;
    border: 1px solid #ccc;
    border-collapse: collapse;
    margin: 0;
    padding: 0;
    width: 100%;
    table-layout: fixed;
  }

  table caption {
    font-size: 1.5em;
    margin: 0.5em 0 0.75em;
  }

  table tr {
    background-color: #f8f8f8;
    border: 1px solid #ddd;
    padding: 0.35em;
  }

  table th,
  table td {
    padding: 0.625em;
    text-align: center;
    width: 200px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  table th {
    font-size: 0.85em;
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  @media screen and (max-width: 600px) {
    table {
      border: 0;
      color: black;
    }

    table caption {
      font-size: 1.3em;
    }

    table thead {
      border: none;
      clip: rect(0 0 0 0);
      height: 1px;
      margin: -1px;
      overflow: hidden;
      padding: 0;
      position: absolute;
      width: 1px;
    }

    table tr {
      border-bottom: 3px solid #ddd;
      display: block;
      margin-bottom: 0.625em;
    }

    table td {
      border-bottom: 1px solid #ddd;
      display: block;
      font-size: 0.8em;
      text-align: right;
    }

    table td::before {
      content: attr(data-label);
      float: left;
      font-weight: bold;
      text-transform: uppercase;
    }

    table td:last-child {
      border-bottom: 0;
    }
  }
</style>
