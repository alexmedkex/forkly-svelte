<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import { lastId } from "./store";
  import { fade, onInput } from "../../../dynamic-list.ts"

  export let number: number;
  export let id = undefined;

  const dispatch = createEventDispatcher();

  const item = {
    value: ''
  }

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
</style>

<div>
  {number}
  <div class="box">
    <input
      class={lastItemId === id ? 'faded' : ''}
      bind:value={item.value}
      in:fade={{ enabled: lastItemId === id }}
      on:input={onInstructionInput}
      type="text"
      placeholder='Add instructions' />
  </div>
</div>
