<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ task.text }}
      <div v-if="showUpdateTask">
        <UpdateTask />
      </div>
      <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
      <i @click="$emit('update-task', updatedTask)" class="fas fa-pencil"
        >update</i
      >
    </h3>
    <h3>{{ task.day }}</h3>
  </div>
</template>

<script>
import UpdateTask from "./UpdateTask";

export default {
  name: "Task",
  props: {
    task: Object,
  },
  components: {
    updateTask,
  },
  data() {
    return {
      showUpdateTask: false,
    };
  },
};
</script>

<style scoped>
.fas {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
