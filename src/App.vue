<template>
  <div class="container">
    <Header />
    <Text @submitted="onSubmitted" />
    <Data :datas="datas" @deleted="listDeleted" />
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import Text from './components/Text.vue';
import Data from './components/Data.vue';

//DATA//
import { ref, onMounted } from 'vue';
const datas = ref([

]);
//FETCH FROM LOCALSTORAGE AND onMOUNTED
onMounted(() => {
  const saveDatas = JSON.parse(localStorage.getItem('datas'));
  if (saveDatas) {
    datas.value = saveDatas;
  }
})
const onSubmitted = (storeData) => {
  datas.value.push({
    id: generateUniqueId(),
    info: storeData.info,
  });
  // console.log(generateUniqueId());
  savelocalStorage();
}
//define generateUniqueId
const generateUniqueId = () => {
  return Math.floor(Math.random() * 10);
}
//List Delete
const listDeleted = (id) => {
  datas.value = datas.value.filter((data) =>
    data.id !== id
  );
  savelocalStorage();
}
//SAVE LOCALSTORAGE
const savelocalStorage = () => {
  localStorage.setItem('datas', JSON.stringify(datas.value));
}
</script>


<style scoped></style>
