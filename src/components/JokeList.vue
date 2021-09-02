<template>
  <div class="joke" v-for="joke in jokes">
    <div>{{ joke.joke }}</div>
  </div>
</template>

<script>
export default {
  props: {
    jokes: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.joke {
  display: flex;
  justify-content: space-between;
  padding: 20px;
  border: 2px solid #5562f5;
  margin-top: 10px;
}
</style>
