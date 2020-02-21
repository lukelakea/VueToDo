<template >
    <div>
          <!-- Rendering active/complete icon -->  
          <div 
          class="entryCompleteStatus" 
          @click="completeEntry(entry)">
          {{entry.entryCompleteStatus}}   
          </div>
          <!--  If user clicks on entry, allows them to edit it -->
          <input 
          v-if = "entry.edit" v-model = "entry.text"
          @blur= "entry.edit = false; $emit('update')"
          @keyup.enter = "entry.edit = false; $emit('update')"
          class="entryText" >
          <div v-else>
            <label :class="[entry.entryCompleteStatus ==='🔵' ? 'styleA' : 'styleB']" @click = "entry.edit = true;">{{entry.text}}</label>  
        </div>
        <!--  Delete Button -->
        <div 
        class="entryDelete"
        @click="deleteEntry(index)">❌</div>
    </div>
</template>

<script>
export default {
    props: {
        entries: Array,
        entry: Object,
        index: Number
    },
    methods: {
        //Edit existing entry
        editEntry: function(entry){
            this.entry = entry;
        },
        //Toggle status of active/completed entry
        completeEntry: function(entry) {
            if(entry.entryCompleteStatus==='🔵'){
                entry.entryCompleteStatus = '✅'}
                else{
                    entry.entryCompleteStatus = '🔵'
                }
            },
            //Delete entry from the list
            deleteEntry: function(index){
                this.entries.splice(index, 1)
            },
    }
   
}
</script>