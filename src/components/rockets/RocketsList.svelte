<script>
  import Rocket from "./Rocket.svelte";
  export let rockets;
</script>

<main>
  <div class="rockets">
    {#each rockets as rocket}
      <Rocket {rocket} />
    {/each}
  </div>
</main>
