<template>
  <div class="container">
    <h1 class="title">Welcome to Vue with Sass!</h1>
    <button class="btn-primary">Click Me</button>
  </div>
</template>

<script>
export default {
  name: "SassExample",
};
</script>

<style lang="scss">
$primary-color: #3498db;
$secondary-color: #e74c3c;

// Mixin definition
@mixin button-styles($color) {
  background-color: $color;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;

  &:hover {
    background-color: darken($color, 10%);
  }
}

.container {
  text-align: center;
  padding: 20px;

  .title {
    color: $primary-color;
    font-size: 2em;
    margin-bottom: 20px;
  }

  .btn-primary {
    @include button-styles($primary-color);
  }
}
</style>
