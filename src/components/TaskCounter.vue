<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
  tasks: Array
})

let fait = ref(0)
let pasFait = ref(0)
props.tasks.forEach((task) => {
  if (task.isComplete) {
    fait.value += 1
  } else {
    pasFait.value += 1
  }
})
console.log(fait, pasFait)

watch(props.tasks, (nouvelleValeur, ancienneValeur) => {
  fait.value = 0
  pasFait.value = 0
  props.tasks.forEach((task) => {
    if (task.isComplete) {
      fait.value += 1
    } else {
      pasFait.value += 1
    }
  })
})
</script>

<template>
  <div id="compteur">
    <h3>Fait: {{ fait }}</h3>
    <h3>A faire: {{ pasFait }}</h3>
  </div>
</template>

<style scoped>
.complete {
  text-decoration: line-through;
}
#compteur {
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 10px;
}
</style>
