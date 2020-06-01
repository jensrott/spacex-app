<script>
  import Spinner from "../../components/layout/Spinner.svelte";
  import { Link } from "svelte-routing";

  import { onMount } from "svelte";
  import axios from "axios";

  const API_URL = "https://api.spacexdata.com/v3";

  export let rocket_id;
  let rocket = {};
  let loading = false;
  let error = "";
  let images = "";

  onMount(() => {
    const url = `${API_URL}/rockets/${rocket_id}`;
    loading = true;

    axios
      .get(url)
      .then(data => {
        console.log(data.data);

        rocket = data.data;
        console.log(data);
      })
      .catch(err => {
        error = err;
      });

    loading = false;
  });

  console.log(rocket_id);
</script>

<style type="text/scss">
  .rocket-detail {
    background-color: #1a1a1b;
    border: 1px solid #343536;
    border-radius: 0.5rem;
    color: #d7dadc;
    padding: 2% 3%;
    margin: 5% 0;
    transition: all 100ms ease-in-out;
    animation: fade 500ms ease-in-out;

    p {
      span {
        font-weight: bold;
      }
    }
  }
</style>

<main>
  {#if loading}
    <Spinner />
  {/if}
  <div class="rocket-detail">
    <h1>{rocket.rocket_name}</h1>
    <p>{rocket.description}</p>
    <p>{rocket.country}</p>
    <p>
      <span>Company:</span>
      {rocket.company}
    </p>
    <p>
      <span>First flight:</span>
      {rocket.first_flight}
    </p>
  </div>
  <Link to="/rockets">Back</Link>

</main>
