<template>
  <div class="app">
    <styled-input placeholder="Введите слово для поиска среди анекдотов..." />
    <joke-list :jokes="jokes" :likes="likes" @liked="likeJoke" />
  </div>
</template>

<script>
import JokeList from "./components/JokeList.vue";
import StyledInput from "./components/UI/StyledInput.vue";
export default {
  components: {
    JokeList,
    StyledInput,
  },
  data() {
    return {
      likes: new Set(),
      jokes: [
        {
          category: "Programming",
          type: "single",
          joke: "Debugging: Removing the needles from the haystack.",
          flags: {
            nsfw: false,
            religious: false,
            political: false,
            racist: false,
            sexist: false,
            explicit: false,
          },
          id: 40,
          safe: true,
          lang: "en",
        },
        {
          category: "Pun",
          type: "single",
          joke:
            'I have these weird muscle spasms in my gluteus maximus.\nI figured out from my doctor that everything was alright:\nHe said "Weird flex, butt okay."',
          flags: {
            nsfw: false,
            religious: false,
            political: false,
            racist: false,
            sexist: false,
            explicit: false,
          },
          id: 82,
          safe: false,
          lang: "en",
        },
        {
          category: "Programming",
          type: "single",
          joke:
            "// This line doesn't actually do anything, but the code stops working when I delete it.",
          flags: {
            nsfw: false,
            religious: false,
            political: false,
            racist: false,
            sexist: false,
            explicit: false,
          },
          id: 12,
          safe: true,
          lang: "en",
        },
        {
          category: "Programming",
          type: "single",
          joke:
            "The six stages of debugging:\n1. That can't happen.\n2. That doesn't happen on my machine.\n3. That shouldn't happen.\n4. Why does that happen?\n5. Oh, I see.\n6. How did that ever work?",
          flags: {
            nsfw: false,
            religious: false,
            political: false,
            racist: false,
            sexist: false,
            explicit: false,
          },
          id: 123,
          safe: true,
          lang: "en",
        },
        {
          category: "Pun",
          type: "single",
          joke:
            "Oysters hate to give away their pearls because they are shellfish.",
          flags: {
            nsfw: false,
            religious: false,
            political: false,
            racist: false,
            sexist: false,
            explicit: false,
          },
          id: 90,
          safe: true,
          lang: "en",
        },
        {
          category: "Pun",
          type: "single",
          joke:
            "I have a joke about trickle down economics, but 99% of you will never get it.",
          flags: {
            nsfw: false,
            religious: false,
            political: false,
            racist: false,
            sexist: false,
            explicit: false,
          },
          id: 238,
          safe: true,
          lang: "en",
        },
        {
          category: "Misc",
          type: "single",
          joke:
            "My wife and I have reached the difficult decision that we do not want children.\nIf anybody does, please just send me your contact details and we can drop them off tomorrow.",
          flags: {
            nsfw: false,
            religious: false,
            political: false,
            racist: false,
            sexist: false,
            explicit: false,
          },
          id: 257,
          safe: true,
          lang: "en",
        },
        {
          category: "Dark",
          type: "single",
          joke:
            'Nowadays people are so sensitive, you can\'t even say "black paint" anymore.\nInstead, you have to say "Jamal, please paint the fence".',
          flags: {
            nsfw: false,
            religious: false,
            political: false,
            racist: true,
            sexist: false,
            explicit: false,
          },
          id: 133,
          safe: false,
          lang: "en",
        },
        {
          category: "Programming",
          type: "single",
          joke:
            'A guy walks into a bar and asks for 1.4 root beers.\nThe bartender says "I\'ll have to charge you extra, that\'s a root beer float".\nThe guy says "In that case, better make it a double."',
          flags: {
            nsfw: false,
            religious: false,
            political: false,
            racist: false,
            sexist: false,
            explicit: false,
          },
          id: 2,
          safe: true,
          lang: "en",
        },
        {
          category: "Pun",
          type: "single",
          joke:
            "I was struggling to figure out how lightning works, but then it struck me.",
          flags: {
            nsfw: false,
            religious: false,
            political: false,
            racist: false,
            sexist: false,
            explicit: false,
          },
          id: 220,
          safe: true,
          lang: "en",
        },
      ],
    };
  },
  methods: {
    likeJoke(id) {
      this.likes.add(id);
    },
  },
  mounted() {
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
