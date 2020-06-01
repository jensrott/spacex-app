<script>
  import Spinner from "../../components/layout/Spinner.svelte";
  import Scroll from "../../components/layout/Scroll.svelte";
  import RocketsList from "../../components/rockets/RocketsList.svelte";

  import { onMount } from "svelte";
  import axios from "axios";

  const API_URL = "https://api.spacexdata.com/v3";

  let rockets = [];
  let loading = false;
  let error = "";

  onMount(() => {
    const url = `${API_URL}/rockets`;
    loading = true;

    axios
      .get(url)
      .then(data => {
        rockets = data.data;
      })
      .catch(err => {
        error = err;
      });

    loading = false;
  });
</script>

<style>
  h1 {
    font-size: 2rem;
    color: #fff;
    font-weight: bold;
  }
</style>

<main>
  {#if loading}
    <Spinner />
  {/if}

  <Scroll />

  <h1>Rockets</h1>

  <RocketsList {rockets} />
</main>
