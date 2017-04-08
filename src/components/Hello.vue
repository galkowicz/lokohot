<template>
  <div class="main-page">
    <img src="../assets/logo.png">
    <h1>{{ msg }}</h1>
    <div class="options container">
      <ul>
        <li>
          <div class="login btn-large btn-block section">
            <router-view to="/register"></router-view>
            LOGIN
          </div>
        </li>
        <div class="new-user btn-large btn-block section">NEW USER</div>
        <div class="on-the-fly btn-large btn-block section">ON THE FLY</div>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
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
    justify-content: center;
  }
  .btn-large {
    flex-basis: content;
  }
</style>
