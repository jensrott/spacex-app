<script>
  import Spinner from "../../components/layout/Spinner.svelte";
  import { Link } from "svelte-routing";

  import { onMount } from "svelte";
  import axios from "axios";
  import moment from "moment";

  const API_URL = "https://api.spacexdata.com/v3";

  export let flight_number;
  let launch = {};
  let loading = false;
  let error = "";

  onMount(() => {
    const url = `${API_URL}/launches/${flight_number}`;
    loading = true;

    axios
      .get(url)
      .then(data => {
        // console.log(data.data);

        launch = data.data;
      })
      .catch(err => {
        error = err;
      });

    loading = false;
  });
</script>

<style>
  .launch-detail {
    background-color: #1a1a1b;
    border: 1px solid #343536;
    border-radius: 0.5rem;
    color: #d7dadc;
    padding: 2% 3%;
    margin: 5% 0;
    transition: all 100ms ease-in-out;
    animation: fade 500ms ease-in-out;
  }
</style>

<main>
  {#if loading}
    <Spinner />
  {/if}
  <div class="launch-detail">
    <h1>{launch.mission_name}</h1>
    <p>
      Launch date: {moment(launch.launch_date_local).format('DD MMM YYYY hh:mm a')}
    </p>
    <!-- <p>
      <span>Launch site:</span>
      {launch.launch_site.launch_site_long}
    </p> -->
  </div>
  <Link to="/launches">Back</Link>

</main>
