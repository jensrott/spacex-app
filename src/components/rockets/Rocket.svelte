<script>
  import { Link } from "svelte-routing";

  export let rocket;
</script>

<style type="text/scss">
  .rocket {
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

    p {
      span {
        font-size: 1.5rem;
        font-weight: bold;
      }
    }

    &:hover {
      transform: scale(1.01);
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
  <div class="rocket">
    <div>
      <p>
        <span>{rocket.rocket_name}</span>
      </p>
      <p>{rocket.country}</p>
      <p>{rocket.company}</p>
    </div>
    <div>
      <Link to="rockets/{rocket.rocket_id}">Detail</Link>
    </div>
  </div>
</main>
