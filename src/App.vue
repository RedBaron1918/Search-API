<template>
  <header>
    <h1>THE<strong>Anime</strong>SearchAPI</h1>
    <form class="search-box" @submit.prevent="SearchAnime">
      <input
        type="search"
        class="search-field"
        placeholder="Search Anime..."
        v-model="search"
      />
    </form>
  </header>

  <main>
    <div class="cards">
      <Cards v-for="anime in animelist" :key="anime.mal_id" :anime="anime" />
    </div>
  </main>
</template>

<script>
import Cards from "./components/Cards.vue";
export default {
  name: "App",
  components: { Cards },
  data() {
    return {
      search: "naruto",
      animelist: [],
    };
  },

  methods: {
    async SearchAnime() {
      const response = await fetch(
        `https://api.jikan.moe/v4/anime?q=${this.search}`
      );
      const data = await response.json();
      this.animelist = data.data;
      console.log(this.animelist);
    },
  },
  created() {
    this.SearchAnime();
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;
}
a {
  text-decoration: none;
}
header {
  padding-top: 50px;
  padding-bottom: 50px;
}
header h1 {
  color: #888;
  text-transform: uppercase;
  font-size: 42px;
  font-weight: 400;
  text-align: center;
  letter-spacing: 2px;
  margin-bottom: 30px;
}
header strong {
  color: #313131;
}
header h1:hover {
  color: #313131;
}
header .search-box {
  display: flex;
  justify-content: center;
  padding-left: 30px;
  padding-right: 30px;
}
header .search-field {
  appearance: none;
  background: none;
  border: none;
  outline: none;
  background-color: #f3f3f3;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
  display: block;
  width: 100%;
  max-width: 600px;
  padding: 15px;
  border-radius: 8px;
  color: #313131;
  font-size: 20px;
  transition: 0.4s;
}
header .search-field::placeholder {
  color: #aaa;
}
header .search-field:focus {
  color: #fff;
  background-color: #313131;
  box-shadow: 0px 0px 0px rgba(0, 0, 0, 0.2);
}
main {
  max-width: 1200px;
  margin: 0 auto;
  padding-left: 30px;
  padding-right: 30px;
}
main .cards {
  display: flex;
  flex-wrap: wrap;
  margin: 0 -8px;
}
</style>
