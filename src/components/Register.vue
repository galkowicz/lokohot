<template>
  <div class="login-form center-align" >
    <div class="options container">
        <div class="username">
          <input v-model="email" id="email" type="text" placeholder="Email...">
        </div>
        <div class="password">
          <input v-model="password" id="password" type="password" placeholder="Password...">
        </div>
        <div class="center-align">
          <button v-on:click="register" id="sign-in">Register</button>
          <button v-on:click="signInWithGoogle" id="sign-in-g">Sign-in with Google</button>
        </div>
    </div>
  </div>
</template>

<script>

  const firebase = require('firebase/app');

  export default {
    name: 'hello',
    data() {
      return {
        msg: 'Welcome to Your Vue.js App',
        email: '',
        password: '',
      };
    },
    methods: {
      register() {
        firebase.auth().createUserWithEmailAndPassword(this.email, this.password)
          .catch((error) => {
            console.log('register error', error);
            if (error.code === 'auth/email-already-in-use') {
              const credntial = firebase.auth.EmailAuthProvider.credential(this.email, this.password);
              this.signInWithGoogle()
                .then(() => {
                  firebase.auth().currentUser.link(credntial)
                    .then((user) => {
                      console.log('Account linking success', user);
                    }, (googleError) => {
                      console.log('Account linking error', googleError);
                    });
                });
            }
          });
        console.debug(this.email);
      },
      signInWithGoogle() {
        const provider = new firebase.auth.GoogleAuthProvider();
        provider.addScope('profile');
        provider.addScope('email');

        return firebase.auth().signInWithPopup(provider)
          .catch((error) => {
            console.log('Google sign in error', error);
          });
      },
    },
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped src="./register.scss"></style>
