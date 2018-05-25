<template>
  <div class="login">
    <div class="container">
      <div class="row">
      <div class="col s6 offset-s3">
      <h1>Login</h1>
      <input type="text" v-model="username"
      placeholder="username">
      <br>
      <br>
      <input type="password" v-model="password"
      placeholder="password">
      <p>anda login sebagai : {{ username }}?</p>
      <button class="waves-effect waves-light btn col s12" type="button" name="button">login</button>
      </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "login",
  data() {
    return {
      username: ""
    };
  }
};
</script>

<style scoped>
</style>
