<script>
  import { onMount } from "svelte";
  import { createEventDispatcher } from "svelte";
  import { data1 } from "../js/data";
  import { data2 } from "../js/data";
  import Modal from "./Modal.svelte";
  import SelectedCard from "./SelectedCard.svelte";
  import Addbutton from "./Addbutton.svelte";
  // import Addcard from "./Addcard.svelte";
  // import InputCard from "./InputCard.svelte";

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

    <Addbutton
      {searchQuery}
      {search}
      {isOpen}
      {toggleModal}
      {cards}
      {handleUpdate}
      {isOpened}
    />
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
  <SelectedCard {selectedCard} {nestedData} {expandContent} {isExpanded} />
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
</style>
