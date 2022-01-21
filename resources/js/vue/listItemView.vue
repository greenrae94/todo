<template>
    <div class="item">

        <input
            type="checkbox"
            @change="updateCheck()"
            v-model="item.completed"
        />

        <span :class="[item.completed ? 'completed' : '', 'itemText']"> {{ item.name }} </span>

        <button @click="activateEditingMode"  class="edit">
            <font-awesome-icon :icon="['fas', 'edit']" />
        </button>

        <button @click="removeItem" class="trashcan" >
            <font-awesome-icon :icon="['fas', 'trash']" />
        </button>
    </div>
    
</template>

<script>
export default{
    props: [item],
    data() {

    }
}
</script>

<style scoped>

</style>