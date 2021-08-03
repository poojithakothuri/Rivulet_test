<template>
 <div>
   <img src="../assets/home.png">
  <h1> {{ msg }} </h1>
   <div class ="main-container">
    <div class="card" style="width:50%">
     <div class="container">
       <h4> <b> {{ this.results.title }} </b></h4>
       <p>{{ this.results.body }}</p>
       <h3> Comments: </h3>
       <h5 v-if="this.comment">{{ this.comment }}</h5>
       <input v-model="cname" type="text" placeholder="write a comment" id="cname">
       <button @click="post" type="button">POST</button>
     </div>
    </div>
   </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Home Page',
      results: {},
      comment: ''
    }
  },
  beforeMount () {
    console.log('before')
    fetch('https://jsonplaceholder.typicode.com/posts/1')
      .then((response) => response.json())
      .then((json) => {
        this.results = json
        console.log('hello', this.results)
      })
    console.log('hi', this.results)
  },
  methods: {
    post: function (event) {
      this.comment = this.cname
      console.log(this.cname)
    }
  }
}
</script>

<style scoped>
.card {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
}
.main-container {
  align-items: center;
  justify-content: center;
  display: flex;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}

.container {
  padding: 2px 16px;
}

</style>
