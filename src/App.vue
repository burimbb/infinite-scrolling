<template>
  <div id="app">
    <comment v-for="(comment, index) in items" :key="index" v-bind="comment"></comment>

    <observer @intersect="intersected()" />
    <router-view/>
  </div>
</template>

<script>
import Observer from './components/Observer';
import Comment from './components/Comment';

export default {
  name: 'App',
  components: { Observer, Comment },

  data(){
    return {
      items: [],
      page: 1,
    }
  },

  methods: {
    async intersected(){
      const results = await fetch(`https://jsonplaceholder.typicode.com/comments?_page=${this.page++}`);
      const items = await results.json();

      this.items = [...this.items, ...items];
      console.log(items);
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
</style>
