<template>
  <div class="context-input">
    <textarea
      class="context-textarea"
      maxlength="500"
      placeholder="e.g., 'These are lecture notes for the course XX, based on textbook XX, version XX.'"
      v-model="contextValue"
      @input="autoResize"
      rows="1"
      :style="{ color: '#fff', overflow: 'hidden' }"
    ></textarea>
    <div class="context-subtext">
      Max characters: 500
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContextInput',
  data() {
    return {
      contextValue: '',
    };
  },
  mounted() {
    this.autoResize();
  },
  methods: {
    autoResize(event) {
      const textarea = event ? event.target : this.$el.querySelector('textarea');
      if (textarea) {
        textarea.style.height = 'auto';
        textarea.style.height = Math.min(textarea.scrollHeight, 200) + 'px'; // max 200px
      }
    },
  },
};
</script>

<style scoped>
.context-input {
  display: flex;
  flex-direction: column;
  gap: 0.7rem;
}
.context-textarea {
  width: 100%;
  max-width: 100%;
  min-height: 2.5em;
  max-height: 200px;
  box-sizing: border-box;
  border-radius: 8px;
  border: 1px solid #23242a;
  padding: 0.9em;
  font-size: 1em;
  background: #23242a;
  color: #fff;
  font-family: inherit;
  transition: border 0.2s;
  word-break: break-word;
  overflow-wrap: break-word;
  resize: none;
  overflow: hidden;
}
.context-textarea::placeholder {
  color: #888;
  opacity: 1;
}
.context-subtext {
  font-size: 0.97em;
  color: #666;
}
</style>
