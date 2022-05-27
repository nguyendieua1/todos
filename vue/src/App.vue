<template>
  <ul>
    <li v-for="item of items" :key="item.id">
      {{ item.text }}
    </li>
  </ul>
</template>

<script>

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
      const res = await axios.get(`http://127.0.0.1:8000/api/todos`);
      this.items = res.data;
      console.log(this.items)
    } catch (error) {
      console.log(error);
    }
  },
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
