<template>
  <div class="main-page">
    <img src="../assets/logo.png">
    <h1>{{ msg }}</h1>
    <div class="options container">
      <router-link to="/"><div class="login btn-large btn-block section">LOGIN</div></router-link>
      <router-link to="/register"><div class="new-user btn-large btn-block section">NEW USER</div></router-link>
      <router-link to="/"><div class="on-the-fly btn-large btn-block section">ON THE FLY</div> </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data() {
    return {
      msg: 'Lo Ko Hot - Fair Teams!',
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
  .container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  .btn-large {
    flex-basis: content;
    font-size: 3rem;
  }
</style>
