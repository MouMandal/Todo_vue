<template>
      <form id="add" @submit.prevent="onSubmit">
            <div class="text">
                  <input type="text" id="info" v-model="info" placeholder="Enter the text">
                  <button id="btn">Add</button>
            </div>
      </form>
</template>

<script setup>
import { ref } from 'vue';
const info = ref("");
const emit = defineEmits(['submitted']);
const onSubmit = () => {
      if (!info.value) {
            return;
      }
      else {
            console.log(info.value);
      }
      const storeData = {
            info: info.value,
      };
      emit('submitted', storeData);

      info.value = '';
}
</script>


