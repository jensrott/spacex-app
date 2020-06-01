<script>
  import Spinner from "../../components/layout/Spinner.svelte";
  import Scroll from "../../components/layout/Scroll.svelte";
  import LaunchesList from "../../components/launches/LaunchesList.svelte";

  import { onMount } from "svelte";
  import axios from "axios";

  const API_URL = "https://api.spacexdata.com/v3";

  let launches = [];
  let loading = true;
  let error = "";

  onMount(() => {
    const url = `${API_URL}/launches`;
    loading = true;

    axios
      .get(url)
      .then(data => {
        let sortedData = data.data.sort((a, b) => {
          return new Date(b.launch_date_local) - new Date(a.launch_date_local);
        });
        launches = sortedData;
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

  <h1>Launches</h1>
  <LaunchesList {launches} />
</main>
