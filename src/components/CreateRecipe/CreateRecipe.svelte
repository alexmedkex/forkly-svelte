<script lang="ts">
  import Ingredients from "./Ingredients/index.svelte";
  import Utensils from "./Utensils.svelte";
  import Instructions from "./Instructions/index.svelte";
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

  .left-section {
    grid-column-start: 1;
  }

  .title {
    font-size: 35px;
  }
</style>

<div class="container">
  <input class="title" placeholder="Recipe title" />

  <div class="left-section">
    <Ingredients />
  </div>

  <div class="left-section">
    <Utensils />
  </div>

  <div class="left-section">
    <Instructions />
  </div>

</div>
