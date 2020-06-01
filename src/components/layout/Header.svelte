<script>
  import { Link } from "svelte-routing";

  let logo = "assets/logo.png";
</script>

<style type="text/scss">
  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    padding: 2% 5%;
    background-color: #000;
    color: #fff;

    &__links {
      color: inherit;
      text-decoration: none;
    }

    &__logo {
      width: 300px;
      height: auto;
    }
  }
</style>

<main>
  <div class="header">
    <Link to="/launches" class="header__links" href="/launches">Launches</Link>
    <Link to="/">
      <img class="header__logo" src={logo} alt="spacex-logo" />
    </Link>
    <Link to="/rockets" class="header__links" href="/rockets">Rockets</Link>
  </div>
</main>
