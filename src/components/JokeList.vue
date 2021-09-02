<template>
  <joke-item v-for="joke in jokes" :joke="joke" :key="joke.id" />
</template>

<script>
import JokeItem from "./JokeItem.vue";
export default {
  components: { JokeItem },
  props: {
    jokes: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped></style>
