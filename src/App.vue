<template>
  <div id="app">
    <div class="container">
      <!-- <img width="25%" src="./assets/Vuejs_Logo.png"> -->
      <br>
      <div class="row">
      <a href="#" class="waves-effect waves-light btn col s6" @click.prevent="currentView='Login'">login</a>
      <a href="#" class="waves-effect waves-light btn col s6" @click.prevent="currentView='Signup'">signup</a>
      <!-- <HelloWorld/> -->
      </div>
      <component :is="currentView"></component>
      
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import Login from "./components/Login";
import Signup from "./components/Signup";

export default {
  name: "App",
  data() {
    return {
      currentView: "Login"
    };
  },
  components: {
    HelloWorld,
    Login,
    Signup
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

a.nav {
  background-color: #999;
  color: white;
  height: 40px;
  display: inline-block;
  line-height: 40px;
  width: 100px;
  text-decoration: none;
  border: solid 1px white;
}
</style>
