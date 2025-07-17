<template>
  <div class="doc-type-selector">
    <select class="doc-type-dropdown" v-model="localSelectedType" @change="emitSelection">
      <option value="" disabled selected>Select document type...</option>
      <option value="lecture">📘 Lecture Notes / Slides</option>
      <option value="legal">⚖️ Legal Document</option>
      <option value="instructional">🛠️ Instructional / Guideline Document (tutorials, how-to, project specs)</option>
      <option value="general">📄 General / Other</option>
    </select>
    <div class="doc-type-subtext">
      AI uses this to apply the right tone, analysis depth, and formatting.
    </div>
  </div>
</template>

<script>
export default {
  name: 'DocumentTypeSelector',
  props: {
    selectedType: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      localSelectedType: this.selectedType,
    };
  },
  watch: {
    selectedType(newVal) {
      this.localSelectedType = newVal;
    },
  },
  methods: {
    emitSelection() {
      this.$emit('update:selectedType', this.localSelectedType);
    },
  },
};
</script>

<style scoped>
.doc-type-selector {
  display: flex;
  flex-direction: column;
  gap: 0.7rem;
}
.doc-type-dropdown {
  width: 100%;
  max-width: 100%;
  box-sizing: border-box;
  border-radius: 8px;
  border: 1px solid #23242a;
  padding: 0.9em;
  font-size: 1em;
  background: #23242a;
  color: #fff;
  font-family: inherit;
  transition: border 0.2s;
  overflow-x: hidden;
}
.doc-type-dropdown option[value=''] {
  color: #888;
}
.doc-type-subtext {
  font-size: 0.97em;
  color: #666;
}
</style>
