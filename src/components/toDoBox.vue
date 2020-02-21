<template>
  <div class="toDoBoxContainer">
    <h1>To Do List</h1>
    <!-- Box to add new entries  -->
    <input v-model="newentry" @keyup.enter="addEntry">
    <!-- List of existing entries  -->
    <ul>
        <li v-for="(entry,index) in entries" 
        :key="index">

        <!-- If filter is applied, show the ones that qualify  -->
        <template  v-if="entry.entryCompleteStatus === filterChoice">
        <ItemEntry :entries="entries" :entry="entry" :index="index"></ItemEntry>
        </template>

        <!-- Default, no filter applied-->
        <template  v-if="filterChoice === ''">
          <ItemEntry :entries="entries" :entry="entry" :index="index"></ItemEntry>
        </template>
        </li>
    </ul>
<!-- Buttons -->
<button @click="noFilter">All</button>
<button @click="uncompletedFilter">Active</button>
<button @click="completedFilter">Completed</button>
<button @click="clearCompleted(entries)">Clear Completed</button>
</div>
</template>


<script>

    import ItemEntry from './Entry.vue'

    export default{
        components: {
          ItemEntry
        },
        props: {
            entries: Array
        },
        data() {
          return{
            filterChoice: '',
            newentry: ''
        }
    },
    methods: {
      //Add entry to the list  
      addEntry: function() {
        if  (this.newentry.length!=0){
            this.entries.push({
                entryCompleteStatus: '🔵',
                text: this.newentry,
                edit: false})
            this.newentry = ''
        }   
    },
        //Default, displaying all entries
        noFilter(){
            this.filterChoice = ''
        },
        //Show only active entries
        uncompletedFilter(){
            this.filterChoice = '🔵'
        },
        //Show only complete entries
        completedFilter(){
            this.filterChoice = '✅'
        },
        //Clear completed entries from list
        clearCompleted(entries){
            for(var k = 0; k < this.entries.length;){
                if(entries[k].entryCompleteStatus==='✅'){
                    this.entries.splice(k, 1)
                    if(k!=0){
                        k--}
                    }
                    else{
                        k++
                    }
                }
            }
        }
    }

</script>
