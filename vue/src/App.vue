<template>
<li v-for="item in items">
    {{ item.category }}
    {{ item.question }}
</li>
</template>

<script>
import axios from 'axios'
export default {
  name: "App",
  data() {
    return {
      items: []
    }
  },
  components: {

  },
   async created() {
    try {
      const res = await axios.get(`https://opentdb.com/api.php?amount=10&category=27&difficulty=hard&type=multiple`);
      this.items = res.data.results;
      console.log(this.items)
    } catch (error) {
      console.log(error);
    }
  },
  methods: {
    showItem(){
      
      console.log(this.items)
      this.items
    }
  }
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
