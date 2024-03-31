<template>
  <SignUpForm />
</template>

<script>
import SignUpForm from "./components/Signup-form"; // changed the casing to match the actual filename
export default {
  name: "App",
  components: { SignUpForm },
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
  background: rgb(255, 191, 162);
}
</style>
