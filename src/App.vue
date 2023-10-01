<template>
  <h1>How to submit forms</h1>
  <SignupFile />
</template>

<script>
import SignupFile from "./components/SignupFile.vue";

export default {
  name: "App",
  components: {
    SignupFile,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  margin: 0;
  background: #eeee;
}
</style>
