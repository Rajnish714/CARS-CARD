<script>
  export let toggleNavigation;
</script>

<!-- Sidenav content -->
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

<style>
</style>
