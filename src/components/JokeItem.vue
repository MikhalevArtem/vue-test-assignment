<template>
  <div class="joke">
    <div>{{ joke.joke }}</div>
    <div class="joke__buttons">
      <styled-button class="like" @click="$emit('liked', joke.id)"
        >Like</styled-button
      >
    </div>
  </div>
</template>

<script>
import StyledButton from "./UI/StyledButton.vue";
export default {
  components: {
    StyledButton,
  },
  props: {
    joke: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.joke {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border: 2px solid #5562f5;
  margin-top: 10px;
  border-radius: 5px;
}
.like {
  align-self: flex-end;
}
</style>
