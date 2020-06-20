<script>
  import Header from "@components/Header.svelte";
  let test = "test";
</script>

<style lang="scss" global>
  @import "@style/global.scss";

  .header {
    margin-bottom: 50px;
  }
</style>

<textarea bind:value={test}></textarea>
{test}

<div class="header">
  <Header />
</div>

<slot />
