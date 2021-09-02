<template>
  <div class="joke" v-for="joke in jokes">
    <div>{{ joke.joke }}</div>
    <div class="joke__buttons">
      <styled-button>Like!</styled-button>
    </div>
  </div>
</template>

<script>
import StyledButton from "./UI/StyledButton.vue";
export default {
  components: { StyledButton },
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
  align-items: center;
  padding: 20px;
  border: 2px solid #5562f5;
  margin-top: 10px;
  border-radius: 5px;
}
</style>
