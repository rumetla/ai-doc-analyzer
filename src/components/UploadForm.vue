<!-- src/components/UploadForm.vue -->
<template>
  <div class="upload-form">
    <input
      type="file"
      accept="application/pdf"
      @change="handleFileChange"
      class="upload-input"
    />
  </div>
</template>

<script>
export default {
  name: 'UploadForm',
  methods: {
    handleFileChange(event) {
      const file = event.target.files[0];
      if (!file) return;
      if (file.type !== 'application/pdf') {
        alert('Only PDF files are supported.');
        return;
      }
      if (file.size > 10 * 1024 * 1024) {
        alert('File size must be less than 10MB.');
        return;
      }
      this.$emit('file-uploaded', file);
    },
  },
};
</script>

<style scoped>
.upload-form {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.upload-input {
  width: 100%;
  color: #fff;
  background: #23242a;
  border: 1px solid #23242a;
  border-radius: 8px;
  padding: 0.7em 0.5em;
  font-size: 1em;
  font-family: inherit;
  margin-top: 0.2em;
}
.upload-input::file-selector-button {
  background: #23242a;
  color: #fff;
  border: 1px solid #646cff;
  border-radius: 6px;
  padding: 0.4em 1em;
  font-size: 1em;
  cursor: pointer;
  transition: background 0.2s;
}
.upload-input::file-selector-button:hover {
  background: #646cff;
  color: #fff;
}
</style>
