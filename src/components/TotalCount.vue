
<template v-for="(entry,index) in entries" :key="index">
    <div>
        <p>{{ getProductQuanlity()}} To Go</p>
        
    </div>

</template>



<script>

    export default{
        props: {
            entries: Array,
            totalUncompleted: Number

        },
       methods: {
         getProductQuanlity () {
             var qty = 0;
             for(var k =0; k < this.entries.length; k++){
              if(this.entries[k].taskCompleteStatus === '🔵'){
                qty++;
              }
             }
             return qty

           }
     }
  }

</script>