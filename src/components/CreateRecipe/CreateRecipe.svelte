<script lang="ts">
  import Ingredients from "../Ingredients/Ingredients.svelte";
  let title = "title";
</script>

<style lang="scss">
  @import "../../style/theme.scss";

  .container {
    display: grid;
    grid: auto / 1fr 1fr;
    background-color: $accent_dark2;
    height: 100vh;
    padding: 30px;
    border-radius: $border-radius;
  }

  .recipe-title {
    font-size: 35px;
  }

  input {
    background-color: $accent_dark2;
    font-size: 35px;
  }
</style>

<div class="container">
  <div class="recipe-title">
    <input bind:value={title} placeholder="Recipe title" />
  </div>
  <Ingredients />
</div>
