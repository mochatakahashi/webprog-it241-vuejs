<template>
  <div class= "strawberry">
    <h2>{{ name }}</h2>
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'Strawberry',
      message: 'I like strawberry'
    }
  }
};
</script>

<style>
  .strawberry {
    border: dashed black 1px;
    display: inline-block;
    margin: 10px;
    padding: 10px;
    background-color: red;
  }

</style>