<script>
  import { createEventDispatcher } from "svelte";
  import { lastId } from "./stores";
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

  function onInput() {
    if (inputs[0].value === "" && inputs[1].value === "") {
      dispatch("clear", {
        id,
      });
    } else {
      dispatch("input", {
        id,
      });
    }
  }

  function fade(node, { enabled, delay = 0, duration = 400 }) {
    if (enabled) {
      const o = +getComputedStyle(node).opacity;

      return {
        delay,
        duration,
        css: (t) => `opacity: ${t * o}`,
      };
    }
  }
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

  input {
    font-size: 15px;
    background: transparent;
  }
</style>

<div class="item">
  {#each inputs as input}
    <input
      class={lastItemId === id ? 'faded' : ''}
      bind:value={input.value}
      in:fade={{ enabled: lastItemId === id }}
      on:input={onInput}
      type="text"
      placeholder={input.placeholder} />
  {/each}
</div>
