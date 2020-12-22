<template>
  <div class="hello">    
    <Todo />
  </div>
</template>

<script>
import Todo from "./../components/Todo.vue";

export default {
  name: 'Home',
  props: { },
  components: {
    Todo
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello{
  min-height: 100vh;  
}

h3 {
  margin: 40px 0 0;
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
