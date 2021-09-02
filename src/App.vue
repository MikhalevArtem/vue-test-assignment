<template>
  <div class="app">
    <styled-input
      placeholder="Введите слово для поиска среди анекдотов..."
      v-model="searchQuery"
    />
    <joke-list :jokes="searchedJokes" :likes="likes" @liked="likeJoke" />
  </div>
</template>

<script>
import axios from "axios";
import JokeList from "./components/JokeList.vue";
import StyledInput from "./components/UI/StyledInput.vue";
export default {
  components: {
    JokeList,
    StyledInput,
  },
  data() {
    return {
      searchQuery: "",
      likes: new Set(),
      jokes: [],
    };
  },
  methods: {
    likeJoke(id) {
      this.likes.add(id);
    },
    async fetchJokes() {
      try {
        const response = await axios.get(
          "https://v2.jokeapi.dev/joke/Any?type=single&amount=10"
        );
        this.jokes = response.data.jokes;
      } catch (e) {
        alert("Произошла ошибка: " + e.message);
      }
    },
  },
  mounted() {
    this.fetchJokes();
    if (localStorage.getItem("likes")) {
      this.likes = new Set(JSON.parse(localStorage.getItem("likes")));
    }
  },
  watch: {
    likes: {
      handler(newLikes) {
        localStorage.setItem("likes", JSON.stringify(Array.from(newLikes)));
      },
      deep: true,
    },
  },
  computed: {
    searchedJokes() {
      return this.jokes.filter((joke) =>
        joke.joke.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
};
</script>

<style>
* {
  margin: 0px;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}
</style>
