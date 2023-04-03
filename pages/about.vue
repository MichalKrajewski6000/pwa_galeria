<template>
  <div>
    <TopNav />
    <h1 class="colorRed">About</h1>
    <button @click="showInfo">Click this button</button>
  </div>
</template>

<script>
import TopNav from "../components/nav/TopNav.vue";
export default {
  name: "AboutPage",
  components: { TopNav },

  methods: {
    showInfo: () => {
      return alert("Eyes up Guardian!");
    },
  },
};
</script>
<style scoped>
.gallery {
  width: 50vw;
}
</style>
