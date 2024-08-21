<script setup>
import {ref, reactive, defineProps, defineEmits, watch} from "vue"
const props = defineProps({sweep : Object})
const emits = defineEmits(['update'])

const onChange = () => {
  emits("update", props.sweep)  
}


</script>

<template>
  <div class="flex-vert gap-10">
    <div class="flex-hori gap-10">
      <p>Pitch: {{ sweep.pitch }}</p>
      <input @change="onChange()" class="pitch-slider" type="range" min="0" max="8" step="1" v-model.number="sweep.pitch"></input>
    </div>

    <div class="flex-hori gap-10">
      <p>A</p>
      <input @change="onChange()" class="slider" type="range" min="0.01" max="1" step="0.01" v-model.number="sweep.envelope.attack" >
    </div>
    
    <div class="flex-hori gap-10">
      <p>D</p>
      <input @change="onChange()" class="slider" type="range" min="0.05" max="2" step="0.01" v-model.number="sweep.envelope.decay">
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