<template>
  <main>
    <h1>{{header}}</h1>
    <h4 id="h4"></h4>
  </main>
</template>

<script>
export default {
  name: "ConverterUi",
  data() {
    return {
      header: "Converter Here"
    };
  }
};
</script>

<style scoped>
main {
  width: 100%;
  border: 2px solid #333;
  padding: 10px;
  height: 600px;
  background: whitesmoke;
}
</style>