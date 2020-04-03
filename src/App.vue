<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"

export default {
  name: "App",
  components: {
    Header,
    Main
  }
}

const firebaseConfig = {
  apiKey: "AIzaSyADzllMPc2M5xkvGGpIJdkdd-o2Oo6Cmmc",
  authDomain: "vue-cli-simple-quiz.firebaseapp.com",
  databaseURL: "https://vue-cli-simple-quiz.firebaseio.com",
  projectId: "vue-cli-simple-quiz",
  storageBucket: "vue-cli-simple-quiz.appspot.com",
  messagingSenderId: "365446265261",
  appId: "1:365446265261:web:5042d7280fe6aab9250924",
  measurementId: "G-KQSH7T1NRB"
}
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
</style>
