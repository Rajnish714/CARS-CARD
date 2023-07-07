<script>
  import { createEventDispatcher } from "svelte";

  let title = "";
  let description = "";

  const dispatch = createEventDispatcher();

  function addCard() {
    const newCard = {
      id: Date.now(), // Generate a unique id for the new card
      title,
      description,
    };

    dispatch("cardAdded", newCard);
    closeModal();
  }

  function closeModal() {
    dispatch("closeModal");
  }
</script>

<div class="modal">
  <div class="modal-content">
    <h2>Add New Card</h2>
    <div class="form-group">
      <label for="title">Title:</label>
      <input type="text" id="title" bind:value={title} />
    </div>
    <div class="form-group">
      <label for="description">Description:</label>
      <textarea id="description" rows="4" bind:value={description} />
    </div>
    <div class="button-group">
      <button class="btn btn-primary" on:click={addCard}>Add Card</button>
      <button class="btn" on:click={closeModal}>Cancel</button>
    </div>
  </div>
</div>

<style>
  input {
    color: black;
  }
  textarea {
    color: black;
  }
</style>
