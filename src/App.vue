<template>
  <div id="app">
    <ToDoBox
    :entries="entries"
    ></ToDoBox>
    <TotalCount
      :entries="entries"
      :totalUncompleted="totalUncompleted"
    ></TotalCount>
  </div>
</template>

<script>
import ToDoBox from './components/toDoBox.vue'
import TotalCount from './components/TotalCount.vue'

export default {
  name: 'App',
  components: {
    ToDoBox,
    TotalCount
  },
  data() {
    return {
     entries: [],
     totalUncompleted: 0
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
  font-size: 20px;
}

input{
  width: 400px;
  height: 40px;
  font-size: 20px;
  padding: 5px;
}

li{
    list-style-type: circle;
    display: flex;
    position: relative;
}

label{
  padding: 10px;
}

ul{
  width: 30vw;
  margin-left:32vw;
}

.entryCompleteStatus{
  cursor: pointer;
}

li:hover .entryDelete{ visibility: visible; }

.entryText{
  margin-left:10px;
  margin-right:30px;
}

.entryDelete{
  right: 0;
  position: absolute;
  cursor: pointer;
  visibility: hidden;
}

.styleA{
  color:black;
}

.styleB{
  color:lightgray;
}

</style>
