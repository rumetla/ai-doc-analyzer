<template>
  <div class="ai-task-selector">
    <label class="task-radio" v-for="task in tasks" :key="task.key">
      <input
        type="radio"
        name="ai-task"
        :value="task.key"
        v-model="localSelectedTask"
        @change="emitSelection"
      />
      <span>{{ task.label }}</span>
    </label>
  </div>
</template>

<script>
export default {
  name: 'AiTaskSelector',
  props: {
    selectedTask: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      tasks: [
        { key: 'summarize', label: 'Summarize' },
        { key: 'bullet_points', label: 'Create Bullet Points' },
        { key: 'explain', label: 'Explain Complex Sections' },
        { key: 'analysis', label: 'Perform In-Depth Analysis' },
        { key: 'translate', label: 'Translate to Simple Language' },
      ],
      localSelectedTask: this.selectedTask,
    };
  },
  watch: {
    selectedTask(newVal) {
      this.localSelectedTask = newVal;
    },
  },
  methods: {
    emitSelection() {
      this.$emit('update:selectedTask', this.localSelectedTask);
    },
  },
};
</script>

<style scoped>
.ai-task-selector {
  display: flex;
  flex-direction: column;
  gap: 0.7rem;
}
.task-radio {
  font-size: 1em;
  color: #e0e0e0;
  display: flex;
  align-items: center;
  gap: 0.7em;
  padding: 0.5em 0.2em;
  border-radius: 6px;
  transition: background 0.2s;
}
.task-radio input[type='radio'] {
  accent-color: #646cff;
  background: #23242a;
  border: 1.5px solid #23242a;
  width: 1.1em;
  height: 1.1em;
  margin-right: 0.5em;
}
.task-radio span {
  color: #e0e0e0;
}
</style>
