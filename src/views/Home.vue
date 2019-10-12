<template>
  <div class="home">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/projects">Projects</router-link>
    </div>
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld class="bg-green-500" msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "home",
  components: {
    HelloWorld
  }
};
</script>

<style scoped>
#nav {
  padding: 30px;
  background-color: rgba(10, 10, 10, 0.3);
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
