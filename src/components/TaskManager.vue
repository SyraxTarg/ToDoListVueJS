<script setup>
const props = defineProps({
  tasks: Array
})
</script>

<template>
  <div>
    <ul v-for="task in tasks" :key="task.id" id="allTasks" class="list-group list-group-flush">
      <li v-show="task.isComplete" class="comp list-group-item">
        <input
          type="checkbox"
          name="complete"
          id="{{ task.id }}"
          checked
          v-model="task.isComplete"
          class="form-check-input"
        />
        <p :class="{ complete: task.isComplete, incomplete: !task.isComplete }">{{ task.task }}</p>
      </li>
      <li v-show="!task.isComplete" class="nocomp list-group-item">
        <input type="checkbox" name="complete" id="{{ task.id }}" v-model="task.isComplete" />
        <p :class="{ complete: task.isComplete, incomplete: !task.isComplete }">{{ task.task }}</p>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.complete {
  text-decoration: line-through;
}
#allTasks {
  list-style: none;
}

.comp,
.nocomp {
  display: flex;
  flex-direction: row;
  gap: 10px;
}
</style>
