<template>
    <div>
        <list-item-edit
            v-if="isEditing"
            :item="item"
            v-on:itemupdated="updateItem(), activateEdit()"
        />
        <list-item-view
            v-else
            :item="item"
            v-on:activateedit="activateEdit()"
        />
        
    </div>
</template>

<script>
import listItemEdit from './listItemEdit.vue'
import listItemView from './listItemView.vue'

export default {
    props:['item'],  
    components: {
        listItemView,
        listItemEdit
    },
    data() {
        return{
            isEditing: false
        }
    },
    methods:{
        updateItem(){
            this.$emit('itemchanged');
        },
        activateEdit(){
            if (this.isEditing){
                this.isEditing = false;
            }else{
                this.isEditing = true;
            }
        }
    }
    
}
</script>

<style scoped>

</style>