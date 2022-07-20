<template>
  <div class="card">
    <p>{{ anime.score }}</p>
    <a :href="anime.url" target="_blank">
      <img :src="anime.images.jpg.image_url" alt="" />
      <h3>{{ anime.title }}</h3>
    </a>
  </div>
</template>

<script>
export default {
  props: ["anime"],
};
</script>

<style scoped>
.card {
  flex: 1 1 33%;
  width: 33%;
  max-width: 33%;
  padding: 0px 8px;
  margin-bottom: 16px;
  position: relative;
}
.card img {
  width: 100%;
  height: 300px;
  border-radius: 16px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
  transition: 0.3s;
}
.card h3 {
  padding: 16px;
  color: #313131;
}

.card h3:hover {
  color: #24c444;
}
.card p {
  position: absolute;
  transition: 0.4s;
  top: 0;
  color: #fff;
  padding: 5px;
  background: #24c444;
  border-radius: 20px;
  font-size: 30px;
}
</style>
