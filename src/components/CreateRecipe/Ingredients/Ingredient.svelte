<script>
  import { createEventDispatcher } from "svelte";
  import { lastId } from "./store";
  import { fade, onInput } from "../../../dynamic-list.ts";

  export let id = undefined;

  const dispatch = createEventDispatcher();

  let lastItemId;

  lastId.subscribe((id) => {
    lastItemId = id;
  });

  const inputs = [
    {
      value: "",
      placeholder: "Ingredient",
    },
    {
      value: "",
      placeholder: "Quantity",
    },
    {
      value: "",
      placeholder: "Measurement",
    },
  ];

  const onIngredientInput = onInput.bind(
    null,
    dispatch,
    id,
    () => inputs[0].value === "" && inputs[1].value === ""
  );
</script>

<style lang="scss">
  .faded {
    opacity: 0.2;
  }

  .item {
    display: grid;
    grid: 1fr / 1fr 1fr 1fr;
    margin-bottom: 10px;
  }
</style>

<div
  class={lastItemId === id ? 'faded item' : 'item'}
  in:fade={{ enabled: lastItemId === id }}
  on:input={onIngredientInput}>
  
  {#each inputs as input}
    <input
      bind:value={input.value}
      type="text"
      placeholder={input.placeholder} />
  {/each}
</div>
