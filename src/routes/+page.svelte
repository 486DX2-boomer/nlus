<script lang="ts">
  import { onMount } from "svelte";

  interface nluObject {
    NLU: number;
    Description: string;
    Article: number;
    Unit: string;
  }

  let nlus: nluObject[] = [];
  let searchTerm = "";
  let filteredNlus: nluObject[] = [];

  onMount(async () => {
    const response = await fetch("/nlus.json");
    nlus = await response.json();
    filteredNlus = nlus;
  });

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

<!-- // ----------------------------------------------------------------------->

<style>
  @import url("https://fonts.googleapis.com/css2?family=Gentium+Book+Plus:ital,wght@0,400;0,700;1,400;1,700&family=Noto+Sans:ital,wght@0,100..900;1,100..900&family=Roboto+Mono:ital,wght@0,100..700;1,100..700&display=swap");

  :root {
    background-color: rgb(238, 218, 204);
  }

  .container {
    max-width: 720px;
    margin: 0 auto;
    padding: 1rem;
  }

  .nlu-description {
    color: rgb(15, 15, 187);
    font-family: "Noto Sans", monospace;
    font-size: 1.2rem;
    margin-right: 8px;
  }

  .nlu-article {
    font-family: "Gentium Book Plus", monospace;
    font-size: 1rem;
    margin-right: 8px;
  }

  .nlu-number {
    font-family: "Roboto Mono", sans-serif;
    font-size: 1.6rem;
    margin-left: 8px;
    margin-right: 16px;
  }

  .nlu-unit {
    font-size: 1rem;
    font-family: "Gentium Book Plus", serif;
    color: rgb(189, 4, 4);
  }

  .searchBox {
    display: flex;
    align-items: center;
    margin-bottom: 1rem;
    padding: 0.5rem;
    background-color: white;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .searchBox input {
    flex: 1;
    padding: 0.5rem;
    font-size: 1rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-right: 0.5rem;
  }

  .searchBox input:focus {
    outline: none;
    border-color: rgb(15, 15, 187);
  }

  .searchBox button {
    padding: 0.5rem 1rem;
    font-size: 1rem;
    border: none;
    background-color: rgb(189, 4, 4);
    color: white;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .searchBox button:hover {
    background-color: rgb(159, 0, 0);
  }

  .nlu-list {
    list-style-type: none;
    padding: 0;
    margin: 0;
  }

  .nlu-list-item {
    display: flex;
    align-items: center;
    padding: 0.5rem;
    margin: 0 auto;
    max-width: 70%;
    margin-bottom: 0.5rem;
    background-color: white;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .nlu-item:last-child {
    margin-bottom: 0;
  }

  .spinner {
    border: 5px solid rgba(0, 0, 0, 0.1);
    border-top: 5px solid #3437db;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    animation: spin 1s linear infinite;
    margin: auto;
    margin-top: 50px;
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
