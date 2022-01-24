<template>
    <div>
        <list-item-view
            :item="item" 
        />
        <list-item-edit
            :item="item"
            v-on:itemupdated="updateItem()"
        />
    </div>
</template>

<script>
import ListItemEdit from './listItemEdit.vue'
import listItemView from './listItemView.vue'

export default {
    props:['item'],
    components:{
        listItemView,
        ListItemEdit
    },
    methods:{
        updateItem(){
            this.$emit('itemchanged');
        }
    }
    
}
</script>

<style scoped>

</style>