<template>
  <joke-item
    v-for="joke in jokes"
    :joke="joke"
    :key="joke.id"
    :class="{ 'liked-joke': likes.has(joke.id) }"
    @liked="$emit('liked', joke.id)"
  />
</template>

<script>
import JokeItem from "./JokeItem.vue";
export default {
  components: { JokeItem },
  emits: ["liked"],
  props: {
    jokes: {
      type: Array,
      required: true,
    },
    likes: {
      type: Set,
      required: true,
    },
  },
};
</script>

<style scoped>
.liked-joke {
  background-color: rgb(105, 230, 116);
}
</style>
