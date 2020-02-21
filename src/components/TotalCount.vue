<template v-for="(entry,index) in entries" :key="index">
    <div>
        <p>{{ countRemainingTotal()}} To Go</p>
    </div>
</template>
<script>
export default {
    props: {
        entries: Array,
        totalUncompleted: Number

    },
    methods: {
        //Counts remaining active entries
        countRemainingTotal() {
            var numLeft = 0;
            for (var k = 0; k < this.entries.length; k++) {
                if (this.entries[k].entryCompleteStatus === '🔵') {
                    numLeft++;
                }
            }
            return numLeft

        }
    }
}
</script>