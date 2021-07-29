<template>
  <form class="add-form" @submit="onSubmit">
    <div class="form-control">
      <label for="text">Task</label>
      <input
        aria-label="text"
        type="text"
        name="text"
        placeholder="Add the task..."
        v-model="text"
        required
      />
    </div>
    <div class="form-control">
      <label for="day">Day</label>
      <input
        aria-label="day"
        type="text"
        name="day"
        placeholder="Add day and time..."
        v-model="day"
      />
    </div>
    <div class="form-control form-control-check">
      <label for="reminder">Set Reminder</label>
      <input
        aria-label="reminder"
        type="checkbox"
        name="reminder"
        v-model="reminder"
      />
    </div>
    <input
      aria-label="submit"
      type="submit"
      value="Save Task"
      class="btn btn-block"
    />
  </form>
</template>
<script>
export default {
  name: 'AddTask',
  data() {
    return { text: '', day: '', reminder: false };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      const newTask = {
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      };
      this.text = '';
      this.reminder = false;
      this.day = '';
      this.$emit('add-task', newTask);
    },
  },
  emits: ['add-task'],
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
