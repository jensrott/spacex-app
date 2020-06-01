<script>
  import { onMount } from "svelte";

  const scrollTop = () => {
    window.scroll({ top: 0, left: 0, behavior: "smooth" });
  };

  onMount(() => {
    const button = document.getElementById("scroll-btn");
    console.log(button);
    window.addEventListener("scroll", () => {
      let y = window.scrollY;
      if (y >= 200) {
        button.style.visibility = "visible";
      } else {
        button.style.visibility = "hidden";
      }
    });
  });
</script>

<style type="text/scss">
  .button {
    background-color: #4193c6;
    color: #fff;
    width: 45px;
    height: 45px;
    display: flex;
    visibility: hidden;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
    position: fixed;
    top: 89%;
    right: 2.7%;
    cursor: pointer;
    transition: all 100ms ease-in-out;

    &:active {
      transform: scale(1.03);
    }

    &:hover {
      transform: scale(0.98);
    }
  }
</style>

<main>

  <div on:click={scrollTop} id="scroll-btn" class="button">
    <i class="fas fa-arrow-up" />
  </div>
</main>
