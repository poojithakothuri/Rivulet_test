<template>
  <div class="hello">
    <img src="../assets/logo.png">
    <h1> {{ msg }} </h1>
    <input v-model="uname" type="text" placeholder="username/email" id="uname" name="uname">
    <br/>
    <br/>
    <button @click="login" type="button">Login</button>
  </div>
</template>

<script>
import Router from '../router/index'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Rivulet '
    }
  },
  methods: {
    login: function (event) {
      if (this.uname === 'poo') {
        Router.push({ name: 'HomePage', params: { userId: 123 } })
      }
    }
  }
}
</script>
