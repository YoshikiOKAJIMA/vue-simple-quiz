<template>
  <div class="header">
    <p>★★★★★{{ title }}★★★★★</p>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return { title: "Quiz Game by Vue CLI" }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
p {
  font: black, 10px;
}
</style>
