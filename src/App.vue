<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1>Vue Resources</h1>
          <div class="form-group">
            <label for="username">Username</label>
            <input type="text" class="form-control" v-model="user.username">
          </div>
          <div class="form-group">
            <label for="mail">Mail</label>
            <input type="email" class="form-control" v-model="user.email">
          </div>
          <button class="btn btn-primary" @click="submitFrm">submit</button>
      </div>
    </div>
    </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      user:{
        username:'',
        email:''
      }
    }
  },
  methods:{
    submitFrm(){

    }
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
