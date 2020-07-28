<script>
  import Item from "./Ingredient.svelte";
  import { lastId } from "./store";
  import { addItem, removeItem } from "../../../dynamic-list.ts";

  let items = [{ id: 0 }];

  const addIngredient = (event) => {
    const newItems = addItem(items, lastId, event);
    if (newItems) {
      items = newItems;
    }
  };
  const removeIngredient = (event) => {
    const newItems = removeItem(items, lastId, event);
    if (newItems) {
      items = newItems;
    }
  };
</script>

<style lang="scss">
  @import "@style/theme.scss";
  .list {
    border-radius: $border-radius;
    background-color: $grey-dark1;
    margin-top: 10px;
    padding: 20px;
  }
</style>

<div>
  Ingredients
  <div class="list">
    <Item />
    {#each items as item (item.id)}
      <Item id={item.id} on:input={addIngredient} on:clear={removeIngredient} />
    {/each}
  </div>
</div>
