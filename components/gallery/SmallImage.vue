<template>
  <div class="thumb">
    <img
      :src="item"
      v-for="(item, index) in images"
      :key="index"
      class="image"
      @click="passImage(item)"
    />
  </div>
</template>
<script>
export default {
  name: "SmallImage",
  props: {
    images: {
      type: Array,
      default: () => [],
    },
  },

  created() {
    console.log(this.images);
  },

  methods: {
    passImage(url) {
      this.$emit("selectedImg", url);
    },
  },
};
</script>
<style scoped>
.thumb {
  display: flex;
  justify-content: center;
  align-items: center;
}

.image {
  width: 200px;
  height: 100px;
  padding: 5px;
  cursor: pointer;
}

.image:hover {
  border: 1px solid cyan;
}
</style>
