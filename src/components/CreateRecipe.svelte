<script lang="ts">
  let title = "title";
  let namez = "world";
</script>

<style lang="scss">
  @import "@style/theme.scss";

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

  .ingredients {
    grid-column-start: 1;
  }
  .ingredients-title {
    font-size: 20px;
  }

  .ingredients-box {
    background-color: $grey;
    border-radius: $border-radius;
  }

  input {
    background-color: $accent_dark2;
    font-size: 35px;
  }
</style>

<input bind:value={namez} />
<h1>Hello {namez}!</h1>

<div class="container">
  <div class="recipe-title">
    <input bind:value={title} placeholder="Recipe title" />
  </div>
  {title}
  <div class="ingredients">
    <div class="ingredients-title">Ingredients</div>
    <div class="ingredients-box">awdw</div>
  </div>
</div>
