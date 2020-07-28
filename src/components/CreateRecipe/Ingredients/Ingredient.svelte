<script>
  import { createEventDispatcher } from "svelte";
  import { lastId } from "./store";
  import { fade, onInput } from "../../../dynamic-list.ts"
  
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

<div class="item">
  {#each inputs as input}
    <input
      class={lastItemId === id ? 'faded' : ''}
      bind:value={input.value}
      in:fade={{ enabled: lastItemId === id }}
      on:input={onIngredientInput}
      type="text"
      placeholder={input.placeholder} />
  {/each}
</div>
