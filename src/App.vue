<template>
  <div id="app">
    <vue-showdown markdown="# Markdown to HTML playground" flavor="github"></vue-showdown>
    <p>This is Markdown to HTML converter styled by GFM(Github Flavor Markdown)</p>
    <p>
      You can see all steps here -
      <a></a>
    </p>
    <playground></playground>
  </div>
</template>

<script>
import Playground from "@/components/Playground";
export default {
  name: "app",
  components: { Playground }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
