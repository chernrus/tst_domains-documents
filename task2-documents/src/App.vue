<template>
  <div class="main">
    <h1>{{ message }}</h1>
    <input v-model="message">
    <AccVerification/>
  </div>
</template>

<script>
import AccVerification from '@/components/AccVerification';

export default {
  name: 'app',
  components: {
    AccVerification
  },
  data () {
    return {
      message: 'Hello Vue.js!'
    }
  }
}
</script>

<style>
body {
  background-color: #f8f8f8;
}

.main {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 0 auto;
  margin-top: 60px;
  width: 90%;

}
</style>
