<script setup>
import {ref, reactive, defineProps, defineEmits, watch} from "vue"
const props = defineProps({
  envelope : Object,
  contour: Number
})
const emits = defineEmits(['update'])

const onChange = () => {
  emits("update", props.envelope) 
}

</script>

<template>
  <div class="flex-vert gap-10">
    
    <div class="flex-hori gap-10">
      <p>D</p>
      <input @change="onChange()" class="slider" type="range" min="0" max="2" step="0.01" v-model.number="envelope.decay">
    </div>

    <div class="flex-hori gap-10">
      <p>S</p>
      <input @change="onChange()" class="slider" type="range" min="0" max="1" step="0.1" v-model.number="envelope.sustain" >
    </div>

  </div>
</template>

<style scoped>
   .env{
    display: flex;
    flex-direction: column;
    border: 0;
    margin: 0;
  }
  input{
    color: black
  }

</style>