<script>
  let date = new Date().getFullYear();
</script>

<style type="text/scss">
  .footer {
    text-align: center;
    padding: 1rem 0;
    background-color: #000;
    color: #fff;
    a {
      text-decoration: none;
      color: #fff;
      font-weight: bold;
      transition: color 300ms ease-in-out;
      animation: fade 500ms ease-in-out;

      &:hover {
        color: #d80258;
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
  <div class="footer">
    <p>
      Copyright © {date}
      <a href="https://github.com/jensrott" target="_blank">Jens Rottiers</a>
      All Rights Reserved.
    </p>
  </div>
</main>
