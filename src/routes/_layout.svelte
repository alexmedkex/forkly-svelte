<script>
  import Header from "../components/Header.svelte";
</script>

<style lang="scss" global>
  @import "@style/global.scss";

  .header {
    margin-bottom: 50px;
  }
</style>

<div class="header">
  <Header />
</div>

<slot />
