<script lang="ts">
  import { getNlus } from "$lib/Nlus.svelte";
  let searchTerm = "";

  const nlus = getNlus();
  let filteredNlus = getNlus();

  function clearSearch() {
    searchTerm = "";
    filteredNlus = nlus;
  }

  function handleFormInput() {
    const term = searchTerm.toLowerCase();
    filteredNlus = nlus.filter((nlu) =>
      nlu.Description.toLowerCase().includes(term)
    );
  }
</script>

<!-- // ----------------------------------------------------------------------->

<div class="container">
  <div class="searchBox">
    <input
      bind:value={searchTerm}
      on:input={handleFormInput}
      placeholder="search the list..."
    />
    <button class="clearButton" on:click={clearSearch}>X</button>
  </div>

  {#if filteredNlus.length > 0}
    <ul class="nlu-list">
      {#each filteredNlus as i}
        <li class="nlu-list-item">
          <span class="nlu-description">{i.Description}</span>
          <span class="nlu-number">{i.NLU}</span>
          <span class="nlu-article">{i.Article}</span>
          <span class="nlu-unit">
            {#if i.Unit.includes("LB")}LRW{/if}
            {#if i.Unit.includes("EA")}each{/if}</span
          >
        </li>
      {/each}
    </ul>
  {:else}
    <!-- Loading spinner -->
    <div class="spinner"></div>
  {/if}
</div>
<footer>
  <!-- This is just a spacer -->
</footer>

<!-- // ----------------------------------------------------------------------->

<style>
  @import url("https://fonts.googleapis.com/css2?family=Gentium+Book+Plus:ital,wght@0,400;0,700;1,400;1,700&family=Noto+Sans:ital,wght@0,100..900;1,100..900&family=Roboto+Mono:ital,wght@0,100..700;1,100..700&display=swap");

  :root {
    --background-color: #ecf6fd;
    --search-background-color: #ecf6fd;
    --search-border-color: #a3d5ff;
    --search-focused-color: #a3d5ff;
    --search-button-color: #f05365;
    --search-button-hover-color: #ca2b3e;
    --shadow-color: #0000001a;
    --item-text-color: #000000;
    --item-number-color: #000000;
    --unit-text-color: #6f73d2;
    --list-background-color: #f0f0fa;
    --list-border-color: #7681b3;
    --spinner-color: #0000001a;
    --spinner-accent-color: #3437db;
    background-color: var(--background-color);
  }

  .container {
    max-width: 720px;
    margin: 0 auto;
    padding: 1rem;
  }

  .nlu-description {
    color: var(--item-text-color);
    font-family: "Noto Sans", monospace;
    font-size: 1.2rem;
    margin-right: 8px;
  }

  .nlu-article {
    color: var(--item-number-color);
    font-family: "Gentium Book Plus", monospace;
    font-size: 1rem;
    margin-right: 8px;
  }

  .nlu-number {
    color: var(--item-number-color);
    font-family: "Roboto Mono", sans-serif;
    font-size: 1.6rem;
    margin-left: 8px;
    margin-right: 16px;
  }

  .nlu-unit {
    color: var(--unit-text-color);
    font-size: 1rem;
    font-family: "Gentium Book Plus", serif;
  }

  .searchBox {
    display: flex;
    padding: 0.5rem;
    background-color: var(--search-background-color);
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 2px 4px #0000001a;
    margin-bottom: 1rem;
    /* position: fixed;
    top: 90%;
    width: 80%; */
  }

  @media screen and (width < 800px) {
    .nlu-description {
      font-size: 1rem;
      margin-right: 3rem;
      min-width: 2rem;
      max-width: 4rem;
    }

    .nlu-number {
      font-size: 1.5rem;
      margin-right: 8px;
    }

    .searchBox {
      display: flex;
      background-color: var(--search-background-color);
      border: 1px solid #ccc;
      border-radius: 8px;
      box-shadow: 0 2px 4px #0000001a;
      position: fixed;
      top: 90%;
      min-width: 90%;
      max-width: 90%;
      padding: 0;
      margin: 0;
    }
  }

  .searchBox input {
    flex: 1;
    padding: 0.5rem;
    font-size: 1rem;
    border: 1px solid #ccc;
    border-radius: 4px;
  }

  .searchBox input:focus {
    outline: none;
    border-color: var(--search-focused-color);
  }

  .searchBox button {
    padding: 0.5rem 1rem;
    margin-left: 0.2rem;
    font-size: 1rem;
    border: none;
    background-color: var(--search-button-color);
    color: white;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .searchBox button:hover {
    background-color: var(--search-button-hover-color);
  }

  .nlu-list {
    list-style-type: none;
    padding: 0;
    margin: 0;
    display: flex-column;
  }

  .nlu-list-item {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0.5rem;
    margin: 0 auto;
    max-width: 80%;
    margin-bottom: 0.5rem;
    background-color: var(--list-background-color);
    border: 1px solid var(--list-border-color);
    border-radius: 8px;
    box-shadow: 0 2px 4px var(--shadow-color);
  }

  .spinner {
    border: 5px solid var(--spinner-color);
    border-top: 5px solid var(--spinner-accent-color);
    border-radius: 50%;
    width: 50px;
    height: 50px;
    animation: spin 1s linear infinite;
    margin: auto;
    margin-top: 50px;
  }

  footer {
    min-height: 4rem;
  }

  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>
