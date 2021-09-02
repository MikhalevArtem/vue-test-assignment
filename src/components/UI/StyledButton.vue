<template>
  <button class="button"><slot></slot></button>
</template>

<script>
export default {};
</script>

<style scoped>
.button {
  background: none;
  padding: 5px 5px;
  border: 2px solid #5562f5;
  border-radius: 5px;
  color: #5562f5;
}
</style>
