<script>
  import Editor from "../Editor/Editor.svelte";
  import Ingredients from "../CreateRecipe/Ingredients/index.svelte";
  import NewSectionButton from "./NewSectionButton/NewSectionButton.svelte";
</script>

<style lang="scss">
  .title {
    font-size: 40px;
    margin-bottom: 20px;
  }

  .ingredients {
    margin-bottom: 20px;
  }
</style>

<input class="title" type="text" placeholder="Title" />
<div class="ingredients">
  <Ingredients />
</div>

<NewSectionButton />

<Editor />
