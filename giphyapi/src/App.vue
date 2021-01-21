<template>
  <div id="app">
    <Search v-on:SearchRequested="handleSearch"></Search>
    <p v-if="isLoading">Loading..</p>
    <Preview :gifs=gifs></Preview>
  </div>
</template>

<script>
import Search from './components/search.vue'
import Preview from './components/preview.vue'

export default {
  name: 'app',
  components: { Search, Preview },
  data() {
    return {
     isLoading: true,
     gifs: []
    }
  },
  methods:{
    doQuery(url){
      fetch(url)
      .then((res) => { return res.json() })
      .then((res) => { 
        this.gifs = res.data; 
        this.isLoading = false;
      })
    },
    handleSearch(query){
      this.isLoading = true;
      this.gifs = [];
      const url = `http://api.giphy.com/v1/gifs/search?q=${query}&api_key=yvpcmkMYnc8GYglZqxe3LRkNfIxGH6iB&limit=20`;
      this.doQuery(url);
    }
  },
  created(){
    const url = 'http://api.giphy.com/v1/gifs/trending?api_key=yvpcmkMYnc8GYglZqxe3LRkNfIxGH6iB&limit=20';
    this.doQuery(url);
  }
  }

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

</style>
