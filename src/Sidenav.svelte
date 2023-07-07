<!-- <script>
  import { onMount } from "svelte";
  import { createEventDispatcher } from "svelte";
  import { data1 } from "./data";
  import { data2 } from "./data";
  import Modal from "./Modal.svelte";
  import Addcard from "./Addcard.svelte";
  import InputCard from "./InputCard.svelte";

  let cards = data1;
  let cardss = data2;
  let isOpen = false;
  let isOpened = false;
  let searchQuery = "";
  let selectedCard = null;
  let nestedData = [];
  let isExpanded = false;

  // const dispatch = createEventDispatcher();

  function toggleNavigation() {
    isOpen = !isOpen;
  }

  function toggleModal() {
    isOpened = !isOpened;
  }

  function search() {
    selectedCard = cards.find(
      (card) => card.title.toLowerCase() === searchQuery.toLowerCase()
    );
    nestedData = cardss.filter((card) => card.companyId === selectedCard.id);
  }

  function ClickedCard(e) {
    selectedCard = e;
    nestedData = cardss.filter((card) => card.companyId === e.id);
    isExpanded = false;
  }

  cards = cards;

  // function addCard(event) {
  //   const newCard = event.detail;
  //   cards = [...cards, newCard];
  // }

  // function openModal() {
  //   dispatch("openModal");
  // }

  function expandContent() {
    isExpanded = true;
  }

  // onMount(() => {
  //   isOpen = false;
  // });

  // function handleModalClose() {
  //   // Handle close modal event if needed
  // }
  function handleUpdate() {
    cards = cards;
  }
</script>

<div class="flex-container">
  <div
    class="{isOpen
      ? 'w-16'
      : 'w-64'} bg-gray-800 text-white transition-width duration-300 sidenav"
  >
    <div class="flex items-center justify-center p-4">
      <button class="text-white" on:click={toggleNavigation}>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          class="h-6 w-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M4 6h16M4 12h16M4 18h16"
          />
        </svg>
      </button>
    </div>

    <div class="p-2">
      <input
        type="text"
        class="w-full mb-2 p-2 border border-gray-300 rounded {isOpen
          ? 'w-0 opacity-0'
          : 'w-full opacity-100'}"
        bind:value={searchQuery}
        placeholder="Search"
        on:input={() => {}}
      />

      <button
        class="w-full p-2 bg-blue-500 text-white rounded {isOpen
          ? 'w-0 opacity-0'
          : 'w-full opacity-100'}"
        on:click={search}
      >
        Search
      </button>

      <main>
        <button
          class="w-full p-2 bg-blue-500 text-white rounded{isOpen
            ? 'w-0 opacity-0'
            : 'w-full opacity-100'}"
          on:click={toggleModal}
        >
          ADD
        </button>
        <Modal {isOpened} {isOpen} {cards} {handleUpdate} />
      </main>
    </div>
    <ul class="p-2">
      {#each cards as card}
        <button class="btn" on:click={() => ClickedCard(card)}>
          <li
            class="cards py-2 px-4 transition-all duration-300 {isOpen
              ? 'w-0 opacity-0'
              : 'w-full opacity-100'}"
          >
            <h5>
              {card.title}
            </h5>
            <p>
              {card.description}
            </p>
          </li>
        </button>
      {/each}
    </ul>
  </div>
  <div class="ml-64 p-4">
    {#if selectedCard}
      <h2 class="text-2xl font-bold mb-4">{selectedCard.title} Nested Data</h2>

      <button class="btn btn-expand" on:click={expandContent}> Expand </button>

      {#if isExpanded}
        {#each nestedData as item}
          <a
            href="#"
            class="block max-w-sm p-6 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700"
          >
            <h5
              class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white"
            >
              {item.title}
            </h5>
            <p class="font-normal text-gray-700 dark:text-gray-400">
              {item.description}
            </p>
          </a>
        {/each}
      {/if}
    {/if}
  </div>
</div>

<style>
  .sidenav {
    margin: 0;
    padding: 0;

    height: fit-content;
  }
  .btn {
    width: fit-content;
    border: none;
  }
  input {
    color: black;
  }

  .ml-64 {
    top: 0;
    text-align: center;
    border-radius: 10px;
  }

  .ml-64 h5 {
    border-bottom: 2px solid white;
    padding-bottom: 10px;
  }

  .cards {
    border: white 2px solid;
    text-align: center;
    margin: 10px;

    width: fit-content;
    cursor: pointer;
    border-radius: 10px;
  }

  .cards h5 {
    border-bottom: white 2px solid;
    width: 100%;
    margin: 5px;
    padding: 5px;
  }

  .cards:hover {
    background-color: rgb(4, 68, 121);
  }

  .btn-expand {
    /* Add styles for the expand button */
  }

  .modal {
    /* Add styles for the modal */
  }

  .modal-content {
    /* Add styles for the modal content */
  }
</style> -->
<script>
  import { onMount } from "svelte";
  import { createEventDispatcher } from "svelte";
  import { data1 } from "./data";
  import { data2 } from "./data";
  import Modal from "./Modal.svelte";
  import Addcard from "./Addcard.svelte";
  import InputCard from "./InputCard.svelte";

  let cards = data1;
  let cardss = data2;
  let isOpen = false;
  let isOpened = false;
  let searchQuery = "";
  let selectedCard = null;
  let nestedData = [];
  let isExpanded = false;

  const dispatch = createEventDispatcher();

  function toggleNavigation() {
    isOpen = !isOpen;
  }

  function toggleModal() {
    isOpened = !isOpened;
  }

  function search() {
    selectedCard = cards.find(
      (card) => card.title.toLowerCase() === searchQuery.toLowerCase()
    );
    nestedData = cardss.filter((card) => card.companyId === selectedCard.id);
  }

  function ClickedCard(e) {
    selectedCard = e;
    nestedData = cardss.filter((card) => card.companyId === e.id);
    isExpanded = false;
  }

  function addCard(event) {
    const newCard = event.detail;
    cards = [...cards, newCard];
  }

  function openModal() {
    dispatch("openModal");
  }

  function expandContent() {
    isExpanded = true;
  }

  onMount(() => {
    isOpen = false;
  });

  function handleModalClose() {
    // Handle close modal event if needed
  }
  function handleUpdate() {
    cards = cards;
  }
</script>

<div class="flex-container">
  <div
    class="{isOpen
      ? 'w-16'
      : 'w-64'} bg-gray-800 text-white transition-width duration-300 sidenav"
  >
    <div class="flex items-center justify-center p-4">
      <button class="text-white" on:click={toggleNavigation}>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          class="h-6 w-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M4 6h16M4 12h16M4 18h16"
          />
        </svg>
      </button>
    </div>

    <div class="p-2">
      <input
        type="text"
        class="w-full mb-2 p-2 border border-gray-300 rounded {isOpen
          ? 'w-0 opacity-0'
          : 'w-full opacity-100'}"
        bind:value={searchQuery}
        placeholder="Search"
        on:input={() => {}}
      />

      <button
        class="w-full p-2 bg-blue-500 text-white rounded {isOpen
          ? 'w-0 opacity-0'
          : 'w-full opacity-100'}"
        on:click={search}
      >
        Search
      </button>

      <main>
        <button
          class="w-full mt-2 p-2 bg-blue-500 text-white rounded{isOpen
            ? 'w-0 opacity-0'
            : 'w-full opacity-100'}"
          on:click={toggleModal}
        >
          ADD
        </button>
        <Modal {isOpened} {isOpen} {cards} {handleUpdate} />
      </main>
    </div>

    <ul class="p-2">
      {#each cards as card}
        <button class="btn" on:click={() => ClickedCard(card)}>
          <li
            class="cards py-2 px-4 transition-all duration-300 {isOpen
              ? 'w-0 opacity-0'
              : 'w-full opacity-100'}"
          >
            <h5>
              {card.title}
            </h5>
            <p>
              {card.description}
            </p>
          </li>
        </button>
      {/each}
    </ul>
  </div>

  <div class="flex-grow p-4">
    {#if selectedCard}
      <div>
        <h2 class="text-2xl font-bold mb-4">
          {selectedCard.title} Nested Data
        </h2>
        <button class="btn btn-expand" on:click={expandContent}>Expand</button>

        {#if isExpanded}
          {#each nestedData as item}
            <a
              href="#"
              class="block max-w-sm p-6 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700"
            >
              <h5
                class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white"
              >
                {item.title}
              </h5>
              <p class="font-normal text-gray-700 dark:text-gray-400">
                {item.description}
              </p>
            </a>
          {/each}
        {/if}
      </div>
    {/if}
  </div>
</div>

<style>
  .flex-container {
    display: flex;
    height: 100vh;
  }
  input {
    color: black;
  }
  .sidenav {
    flex: 0 0 auto;
  }

  .btn {
    width: fit-content;
    border: none;
  }

  .cards {
    border: white 2px solid;
    text-align: center;
    margin: 10px;
    width: fit-content;
    cursor: pointer;
    border-radius: 10px;
  }

  .cards:hover {
    background-color: rgb(4, 68, 121);
  }

  .btn-expand {
    /* Add styles for the expand button */
  }

  .modal {
    /* Add styles for the modal */
  }

  .modal-content {
    /* Add styles for the modal content */
  }
</style>
