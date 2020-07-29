<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import { lastId } from "./store";
  import { fade, onInput } from "../../../dynamic-list.ts";

  export let number: number;
  export let id = undefined;

  const dispatch = createEventDispatcher();

  const item = {
    value: "",
  };

  let lastItemId;

  lastId.subscribe((id) => {
    lastItemId = id;
  });

  const onInstructionInput = onInput.bind(
    null,
    dispatch,
    id,
    () => item.value === ""
  );
</script>

<style lang="scss">
  @import "@style/theme.scss";
  .box {
    border-radius: $border-radius;
    background-color: $grey-dark1;
    margin-top: 10px;
    padding: 20px;
  }

  .faded {
    opacity: 0.2;
  }

  .rounded {
    border: 1px solid $accent-dark1;
    border-radius: 8px;
    margin: 20px 50px;
    opacity: 30%;
  }
</style>

<div
  in:fade={{ enabled: lastItemId === id }}
  on:input={onInstructionInput}
  class={lastItemId === id ? 'faded instruction' : 'instruction'}>
  {number}
  <div class="box">
    <input bind:value={item.value} type="text" placeholder="Add instructions" />
  </div>
  <hr class="rounded" />
</div>
