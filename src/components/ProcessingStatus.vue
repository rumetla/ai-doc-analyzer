<template>
  <div class="processing-status">
    <div class="spinner"></div>
    <div class="status-text">Processing your document...</div>
  </div>
</template>

<script>
export default {
  name: 'ProcessingStatus',
};
</script>

<style scoped>
.processing-status {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.7rem;
  min-height: 60px;
  background: transparent;
}
.spinner {
  width: 32px;
  height: 32px;
  border: 4px solid #23242a;
  border-top: 4px solid #646cff;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}
@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
.status-text {
  color: #e0e0e0;
  font-weight: 500;
  font-size: 1.05em;
}
</style>
