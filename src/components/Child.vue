<script setup lang="ts">
import { defineEmits, watch } from "vue"

const emit = defineEmits(['parentMethod', 'update:isUpdatedData'])

const childMethod = () => {
  alert('child is called');
}

defineExpose({
  childMethod,
});

const triggerParentMethod = () => {
  emit('parentMethod');
}

const props = defineProps({
  data: {
    type: Object,
  }
});

const modifyData = () => {
    emit("update:isUpdatedData", {name: "Jhon Rey", Age: 31});
}

</script>
<template>
  <div>
    <p><button type="button" @click="triggerParentMethod">Call Parent Method</button></p>
    
    <p><button type="button" @click="modifyData">Update New Data</button></p>
    
    <p><slot /></p>
    <p>{{props}}</p>
  </div>
</template>