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

html{
  background-color: #1e2a37;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 18px;
  color: white;
  letter-spacing: 0.5px;
  
}

input{
  width: 400px;
  height: 40px;
  font-size: 18px;
  padding: 5px;
  background: #3a5168;
  color: white;
  outline: none;
  border: none;
}

input.entryText{
  height: 12px;
  margin-left: 23px;
  width: 100%;
}

li{
  display: flex;
  position: relative;
  margin-bottom: 8px;
}

li:empty { 
  margin:0; 
}

label{
  padding-left: 28px;
}

ul{
  width: 30vw;
  margin-left:32vw;
}

button{
  font-size: 15px;
  color: white;
  width: 10em;
  height: auto;
  line-height: 3;
  background: #2c3e50;
  overflow: hidden;
  border-radius: .25em;
  margin: 1vw;
  background: #3a5168;
  border: none;
  font-size: 16px;
}

.entryCompleteStatus{
  cursor: pointer;
  user-select: none;
  position: absolute;
}

li:hover .entryDelete{ 
  visibility: visible;
  opacity: 1;
  transition: opacity .15s ease-out;
}

.entryText{
  margin-left:10px;
  margin-right:30px;
}

.entryDelete{
  right: 0;
  top: 0;
  position: absolute;
  cursor: pointer;
  visibility: hidden;
  opacity: 0;
  transition: opacity .15s ease-out;
  position: absolute;
}

.styleA{
  color: white;
  transition: color .15s ease-out;
}

.styleB{
  color:gray;
  transition: color .15s ease-out;
}

</style>
