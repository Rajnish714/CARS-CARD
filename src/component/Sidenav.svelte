<script>
  import { onMount } from "svelte";
  import { createEventDispatcher } from "svelte";
  import { data1 } from "../js/data";
  import { data2 } from "../js/data";

  import SelectedCard from "./SelectedCard.svelte";
  import Addbutton from "./Addbutton.svelte";
  import Navcard from "./Navcard.svelte";
  import Hambutton from "./Hambutton.svelte";

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

  function ClickedCard(e) {
    selectedCard = e;
    nestedData = cardss.filter((card) => card.companyId === e.id);
    isExpanded = false;
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

  function search() {
    selectedCard = cards.find(
      (card) => card.title.toLowerCase() === searchQuery.toLowerCase()
    );

    console.log(selectedCard);

    nestedData = cardss.filter((card) => card.companyId === selectedCard.id);
  }
  function searchedcard(selected, nested) {
    selectedCard = selected;
    nestedData = nested;
    console.log("clikdedd", a, "nestedcard", b);
  }
</script>

<main id="main">
  <div class="sidenav grid grid-cols-2">
    <div
      class="{isOpen
        ? 'w-16'
        : 'w-64'} bg-gray-800 text-white transition-width duration-300 sidenav"
    >
      <!-- Sidenav content -->
      <Hambutton {toggleNavigation} {isOpen} />

      <Addbutton
        {searchQuery}
        {selectedCard}
        {search}
        {cardss}
        {isOpen}
        {toggleModal}
        {cards}
        {handleUpdate}
        {isOpened}
        {searchedcard}
      />
      <Navcard {cards} {ClickedCard} {isOpen} />
    </div>
    <div class="...">
      <SelectedCard {selectedCard} {nestedData} {expandContent} {isExpanded} />
      <!-- SelectedCard content -->
    </div>
  </div>
</main>

<style>
  #main {
    height: fit-content;
    overflow-y: auto;
    background-color: blanchedalmond;
    overflow: hidden;
  }

  .sidenav {
    /* grid-template-rows: auto 1fr; */
    grid-template-columns: auto 1fr;
    min-height: 100vh;
  }
</style>
