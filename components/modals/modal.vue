<template>
  <div class="modal">
    <div class="modal-content"></div>
  </div>
</template>

<script>
export default {
  name: "Modal",

  methods: {},
};
</script>
<style scoped>
.modal {
  display: flex;
  position: absolute;
  left: 0;
  top: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(255, 255, 255, 0.7);
}

.modal-content {
  background-color: white;
  width: 80%;
  height: 80%;
}
</style>
