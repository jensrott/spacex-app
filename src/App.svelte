<script>
  import Header from "./components/layout/Header.svelte";
  import Footer from "./components/layout/Footer.svelte";

  import Launches from "./views/launches/Launches.svelte";
  import Rockets from "./views/rockets/Rockets.svelte";
  import LaunchesDetail from "./views/launches/LaunchesDetail.svelte";
  import RocketsDetail from "./views/rockets/RocketsDetail.svelte";

  import { Router, Route } from "svelte-routing";

  export let url = "";
</script>

<style type="text/scss">
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  .container {
    max-width: 1440px;
    margin: 0 10%;
  }
</style>

<main>
  <Router {url}>
    <Header />
    <div class="container">
      <Route path="/" component={Rockets} />
      <Route path="/launches" component={Launches} />
      <Route path="/launches/:flight_number" component={LaunchesDetail} />
      <Route path="rockets" component={Rockets} />
      <Route path="rockets/:rocket_id" component={RocketsDetail} />
    </div>
    <Footer />
  </Router>
</main>
