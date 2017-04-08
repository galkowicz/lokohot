<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
  import Firebase from 'firebase';

  function firebaseInit() {
    const config = {
      apiKey: 'AIzaSyBqXRfB0XrFLDIbndmRgI-pdtmQ_I_3eLc',
      authDomain: 'lokohot-fb.firebaseapp.com',
      databaseURL: 'https://lokohot-fb.firebaseio.com',
      projectId: 'lokohot-fb',
      storageBucket: 'lokohot-fb.appspot.com',
      messagingSenderId: '245766400016',
    };

    const app = Firebase.initializeApp(config);
    const db = app.database();
    const users = db.ref('users');
    console.debug(db);
    console.debug(users);

    users.on('value', (snapshot) => {
      snapshot.forEach((childSnapshot) => {
        const childData = childSnapshot.val();
        console.debug(childData);
      });
    });
  }
  firebaseInit();

export default {
    name: 'app',
};
</script>

<style src="./main.scss"></style>
