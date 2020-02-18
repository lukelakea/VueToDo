<template>
  <div class="toDoBoxContainer">
    <h1>To Do List:</h1>
    <input v-model="newEntry" @keyup.enter="addEntry">
    <ul>
        <li v-for="(entry,index) in entries" 
        :key="index">
        <template  v-if="entry.taskCompleteStatus === filterChoice">
          <div 
          class="entryCompleteStatus" 
          @click="completeTask(entry)"
          >
          {{entry.taskCompleteStatus}}   
      </div>
      <input 
      v-if = "entry.edit" v-model = "entry.text"
      @blur= "entry.edit = false; $emit('update')"
      @keyup.enter = "entry.edit = false; $emit('update')"
      class="entryText" >
      <div v-else>
        <label :class="[entry.taskCompleteStatus ==='🔵' ? 'styleA' : 'styleB']" @click = "entry.edit = true;">{{entry.text}}</label>  
    </div>
    <div 
    class="entryDelete"
    @click="deleteTask(index)">❌</div>
</template>

<template  v-if="filterChoice === ''">
  <div 
  class="entryCompleteStatus" 
  @click="completeTask(entry)"
  >
  {{entry.taskCompleteStatus}}   
</div>
<input 
v-if = "entry.edit" v-model = "entry.text"
@blur= "entry.edit = false; $emit('update')"
@keyup.enter = "entry.edit = false; $emit('update')"
class="entryText" >
<div v-else>
    <label :class="[entry.taskCompleteStatus ==='🔵' ? 'styleA' : 'styleB']" @click = "entry.edit = true;">{{entry.text}}</label>  
</div>
<div 
class="entryDelete"
@click="deleteTask(index)">❌</div>
</template>

</li>
</ul>
<button @click="noFilter">All</button>
<button @click="uncompletedFilter">Active</button>
<button @click="completedFilter">Completed</button>
<button @click="clearCompleted(entries)">Clear Completed</button>
</div>
</template>


<script>
    export default{
        props: {
            entries: Array
        },
        data() {
          return{
            filterChoice: '',
            newEntry: ''
        }
    },
    methods: {
      addEntry: function() {
        if  (this.newEntry.length!=0){
            this.entries.push({
                taskCompleteStatus: '🔵',
                text: this.newEntry,
                edit: false})
            this.newEntry = ''
        }   
    },
    editTask: function(entry){
        this.entry = entry;
    },
    completeTask: function(entry) {
        if(entry.taskCompleteStatus==='🔵'){
            entry.taskCompleteStatus = '✅'}
            else{
                entry.taskCompleteStatus = '🔵'
            }
        },
        deleteTask: function(index){
            console.log(index)
            this.entries.splice(index, 1)
        },
        noFilter(){
            this.filterChoice = ''
        },
        uncompletedFilter(){
            this.filterChoice = '🔵'
        },
        completedFilter(){
            this.filterChoice = '✅'
        },
        clearCompleted(entries){
            for(var k = 0; k < this.entries.length;){
                console.log(entries[k].taskCompleteStatus)
                if(entries[k].taskCompleteStatus==='✅'){
                    this.entries.splice(k, 1)
                    if(k!=0){
                        k--}
                    }
                    else{
                        k++
                    }
                }
            },
            log(item){
                console.log(item)
            }
        }
    }

</script>
