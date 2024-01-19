<template>
    <div class="data">
        <div v-for="data in datas" :key="data.id" :class="data">{{ data.info}} <button @click="deleteList(data.id)" class="delete_btn">x</button></div>

    </div>
</template>
<script setup>
import { defineProps } from 'vue';
const emit = defineEmits(['deleted'])
const props = defineProps({
    datas: {
        type: Array,
        required: true,
    },
})
//DELETE THE LIST
const deleteList = (id) => {
    emit('deleted', id);
}
</script>


