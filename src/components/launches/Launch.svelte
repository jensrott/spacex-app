<script>
  import { Link } from "svelte-routing";

  export let launch;
</script>

<style type="text/scss">
  .launch {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    background-color: #1a1a1b;
    border: 1px solid #343536;
    border-radius: 0.5rem;
    color: #d7dadc;
    padding: 2% 3%;
    margin: 5% 0;
    transition: all 100ms ease-in-out;
    animation: fade 500ms ease-in-out;

    &__success {
      color: #55cb20;
    }

    &__failed {
      color: #d80258;
    }

    &:hover {
      transform: scale(1.01);
    }

    p {
      span {
        font-size: 1.5rem;
        font-weight: bold;
      }
    }

    @keyframes fade {
      0% {
        opacity: 0;
        transform: translateY(40px);
      }
      100% {
        opacity: 1;
        transform: translateY(0);
      }
    }
  }
</style>

<main>
  <div class="launch">
    <div>
      <p
        class={launch.launch_success === true ? 'launch__success' : 'launch__failed'}>
        <span>{launch.mission_name}</span>
      </p>
      <!-- <p>{launch.launch_success === true ? 'Succes' : 'Failed'}</p> -->
      <p>{launch.launch_year}</p>
    </div>
    <div>
      <Link to="/launches/{launch.flight_number}">Detail</Link>
    </div>
  </div>
</main>
