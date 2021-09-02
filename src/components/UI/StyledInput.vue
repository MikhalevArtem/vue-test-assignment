<template>
  <input :value="modelValue" @input="updateInput" class="input" type="text" />
</template>

<script>
export default {
  props: {
    modelValue: [String, Number],
  },
  methods: {
    updateInput(event) {
      this.$emit("update:modelValue", event.target.value);
    },
  },
};
</script>

<style scoped>
.input {
  padding: 10px;
  width: 100%;
  border: 2px solid #5562f5;
  border-radius: 5px;
}
</style>
