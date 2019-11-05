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
          <hr>
          <button class="btn btn-primary" @click="fetchData">Get Data</button>
          <ul class="list-group">
            <li class="list-group-item" v-for="user in users">
                {{user.username}} - {{ user.email}}
            </li>
          </ul>
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
      },
      users:[]
    }
  },
  methods:{
    submitFrm(){
      this.$http.post('baseurl/data.json', this.user)
                 .then((res)=>{
                   console.log('res::',res);
                 },error=>{
                   console.log('Error::',error);
                 });
    },
    fetchData(){
      this.$http.get('baseurl/data.json')
                .then((res)=>{
                    return res.json();
                },error=>{
                  console.log(' Error',error);
                }).then((data)=>{
                    const resultArray  = [];
                    for(let key in data){
                      resultArray.push(data[key]);
                    }
                    this.users = resultArray;
                })
                .catch((error)=>{
                    console.log('Catch Error',error);
                });
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
