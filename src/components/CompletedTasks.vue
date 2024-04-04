<script setup>
const props = defineProps({
  tasks: Array
})
</script>

<template>
  <div>
    <ul v-for="task in tasks" :key="task.id" class="list-group list-group-flush" id="completedList">
      <li v-show="task.isComplete" class="list-group-item">
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
    </ul>
  </div>
</template>

<style scoped>
.complete {
  text-decoration: line-through;
}
#completedList {
  box-shadow: 2px 2px rgba(178, 178, 179, 0.678);
}
</style>
