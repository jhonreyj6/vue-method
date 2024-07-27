<script setup lang="ts">
import { ref, watch } from "vue";
import Child from "./components/Child.vue";

const parentMethod = () => {
  alert('parent is called');
}

const childRef = ref(null);

const callChildMethod = () => {
  if (childRef.value) {
    childRef.value.childMethod();
  }
}; 

const myData = ref({
    name: "yer",
    age: 30,
});

const updatedData = ref();

watch(updatedData, () => {
  myData.value = updatedData.value;
})

</script>

<template>
  <div>
    <button type="button" @click="callChildMethod" style="margin-bottom: 14px">Call Child Method</button>
    <child @parentMethod="parentMethod" :data="myData" v-model:isUpdatedData="updatedData" ref="childRef">Children</child>
  </div> 
</template>

<style scoped>

</style>
