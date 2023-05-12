<template>
  <div class="nav">
    <NuxtLink class="nav-item" to="/">Strona Główna</NuxtLink>
    <NuxtLink class="nav-item" to="/gallery">Galeria</NuxtLink>
    <NuxtLink class="nav-item" to="/about">O nas</NuxtLink>
    <NuxtLink class="nav-item" :to="'/cayde/' + name">Cayde-6</NuxtLink>
    <NuxtLink class="nav-item" to="/nasa">Nasa</NuxtLink>
  </div>
</template>

<script>
export default {
  name: "NavPage",

  data() {
    return {
      name: "cayde",
    };
  },
};
</script>
<style scoped>
.nav-item {
  border-radius: 10px;
  border: 2px solid black;
  background-color: antiquewhite;
  padding: 5px;
  margin: auto;
}

.nav-item:hover {
  color: violet;
  background-color: orangered;
}

.nav {
  background-color: silver;
  padding: 10px;
  margin: 0;
  display: flex;
}
</style>
