<template>
    <div class="edit">
        <input v-model="item.name" type="text" />
        <font-awesome-icon 
            icon="plus-square" 
            @click="updateEdit()"
            :class="[item.name ? 'active' : 'inactive', 'plus']"
        />
    </div>
</template>

<script>
export default {
    props:['item'],
    methods:{
        updateEdit() {
            if( this.item.name == '') {
                return;
            }
            
            axios.put('api/item/' + this.item.id, {
                item: this.item
            })
            .then( response => {
                if( response.status == 200){
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
input {
    background: #f7f7f7;
    border: 0px;
    outline: none;
    padding: 5px;
    margin-right: 10px;
    width: 100%;
}
.edit{
    display: flex;
    justify-content: center;
    align-items: center;
}
.plus {
    font-size: 20px;
}
.active {
    color: #00ce25;
}
.inactive {
    color: #999999;
}
</style>