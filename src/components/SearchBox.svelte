<style lang="scss">
  @import "@style/global.scss";
  @import "@style/theme.scss";

  input {
    border-radius: $border-radius;
    border: 2px solid $main;
    color: $text;
    padding: 8px;
    font-size: 15px;
    height: 40px;
    width: 100%;
    background-color: $background;
  }
  input:empty:before {
    content: attr(placeholder);
    color: #ccc;
    opacity: 50%;
  }
  input:focus {
    outline: none;
  }
</style>

<div>
  <input placeholder="Search for a recipe" />
</div>
