<template>
  <button
    class="generate-btn"
    :disabled="disabled"
    :aria-disabled="disabled ? 'true' : 'false'"
    @click="handleClick"
  >
    🚀 Generate AI Report
  </button>
</template>

<script>
export default {
  name: 'GenerateButton',
  props: {
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleClick(event) {
      if (this.disabled) {
        event.preventDefault();
        return;
      }
      this.$emit('click', event);
    },
  },
};
</script>

<style scoped>
.generate-btn {
  width: 100%;
  padding: 1.3em 0;
  font-size: 1.18em;
  font-weight: 700;
  background: linear-gradient(90deg, #646cff 0%, #23242a 100%);
  color: #fff;
  border: none;
  border-radius: 12px;
  margin-top: 0.5em;
  margin-bottom: 0.5em;
  cursor: pointer;
  opacity: 1;
  box-shadow: 0 2px 8px 0 rgba(0,0,0,0.10);
  transition: background 0.2s, opacity 0.2s, cursor 0.2s;
}
.generate-btn:disabled,
.generate-btn[aria-disabled='true'] {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
