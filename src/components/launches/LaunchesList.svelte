<script>
  import Launch from "./Launch.svelte";
  export let launches;
</script>

<main>
  <div class="rockets">
    {#each launches as launch}
      <Launch {launch} />
    {/each}
  </div>
</main>
