<template>
  <div id="app">
    <img src="assets/logo.png">
    <h1>{{ msg }}</h1> 
    <form>
      <idex-input label="Name" type="text"></idex-input>
      <idex-input label="e-Mail" type="email" :width="400"></idex-input>    
      <idex-input label="Nachricht" type="message" :height="200" :width="300"></idex-input>
    </form>    
  </div>
</template>

<script>
import Input from './components/Input.vue'
export default {
  name: 'app',
  data () {
    return {
      msg: 'IDEx Kontakt Formular'
    }
  },
  components:{
    idexInput: Input
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

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
</style>
