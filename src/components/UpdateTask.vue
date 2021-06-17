<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <!-- v-model binds inputs with data -->
      <input
        type="text"
        name="text"
        v-text="text"
        v-model="text"
        placeholder="Add Task"
      />
    </div>
    <div class="form-control">
      <label>Day and Time</label>
      <input
        type="text"
        name="day"
        v-text="day"
        v-model="day"
        placeholder="Add Day and Time"
      />
    </div>
    <div class="form-control">
      <label>Set Reminder</label>
      <input
        type="checkbox"
        name="reminder"
        v-text="reminder"
        v-model="reminder"
      />
    </div>
    <input type="submit" value="Update Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: UpdateTask,
  data() {
    return {
      text: this.text,
      day: this.day,
      reminder: this.reminder,
    };
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
