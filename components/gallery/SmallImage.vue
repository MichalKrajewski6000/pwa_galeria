<template>
  <div class="thumb">
    <img
      v-for="item in images"
      :src="item.url"
      :key="item.id"
      class="image"
      @click="passImage(item.id)"
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
    passImage(id) {
      this.$emit("selectedImg", id);
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
