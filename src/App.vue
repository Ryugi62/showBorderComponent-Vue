<template>
  <BorderComponent />

  <div class="test">
    <h1>Hello world</h1>
  </div>
</template>

<script>
import BorderComponent from "./components/Border.vue";

export default {
  name: "AppComponent",

  components: {
    BorderComponent,
  },
};
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
  outline: 0;
}
</style>
