<template>
<div>
    <list-item-view
        :item='item'

    />
    <list-item-edit
    />


    <div class="editItem" v-show="isEditing" @keyup.enter="updateEdit(); deactiveEditngMode();">
        <input v-model="item.name" type="text" />
        <font-awesome-icon 
        icon="plus-square"
        @click="updateEdit(); deactiveEditngMode();"
        :class="[item.name ? 'active' : 'inactive', 'plus']"
        />
    </div>
</div>
</template>

<script>
import listItemView from "./listItemView.vue";
import listItemEdit from "./listItemEdit.vue"

export default{
    props: ['item'],
    data() {
        return {
            isEditing: false
        }
    },
    components:{
        listItemView,
        listItemEdit
    },
    methods: {
        updateCheck() {
            axios.put('api/item/' + this.item.id, { 
                item: this.item
            })
            .then( response => {
                if( response.status == 200 ){
                    this.$emit('itemchanged');
                }
            })
            .catch( error => {
                console.log( error );
            })
        },
        removeItem() {
            axios.delete('api/item/' + this.item.id)
            .then( response => {
                if( response.status == 200 ){
                    this.$emit('itemchanged');
                }
            })
            .catch ( error => {
                console.log( error );
            })
        },
        activateEditingMode(){
            this.isEditing = true;
        },
        deactiveEditngMode(){
            this.isEditing = false;
        },
        updateEdit(){
            if( this.item.name == '') {
                return;
            }
            axios.put('api/item/' + this.item.id, {
                item: this.item
            })
            .then( response => {
                if( response.status == 200 ){
                    this.$emit('itemupdated');
                }
            })
            .catch( error => {
                console.log( error );
            })
        }
    }
}
</script>

<style scoped>

</style>