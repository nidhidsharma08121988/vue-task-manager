<template name="Header">
  <header>
    <h1>{{ heading }}</h1>
    <Button
      @btn-click="$emit('toggle-add-task')"
      :text="showAddTask ? 'Close' : 'Add Task'"
      :color="showAddTask ? 'red' : 'green'"
    />
  </header>
</template>

<script>
import Button from './Button.vue';
export default {
  name: 'Header',
  props: {
    heading: String,
    showAddTask: Boolean,
  },
  components: {
    Button,
  },
  emits: ['toggle-add-task'],
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
