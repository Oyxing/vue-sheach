<template>
  <div class="hello">

   <input type="text" name="user_email"  v-model = "input_data" @keyup="BtnData()"/>
   <p>{{input_data}}</p>

        <ul>
        <li v-for="item in data">
          <p> {{item.goods_name}}</p>
        </li>
        </ul>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      data:{},
      input_data:''
    }
  },
  created(){
    this.GetData()
  },
  methods:{
    BtnData(){
      console.log(this.input_data)
    },
    GetData(){
      this.$http.get('http://h6.duchengjiu.top/shop/api_goods.php')
        .then((res)=>{
          this.data = res.data.data
          console.log(res)
        })
        .catch((error)=>{
          console.log(error)
        })
    }
  },
  weach:{
    'input_data':'BtnData'  }
}
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
</style>
