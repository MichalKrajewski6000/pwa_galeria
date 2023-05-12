<template>
  <div>
    <navTopNav />
    <Nuxt />
    <modalsNasaModal v-if="modal.opened">
      <img :src="modal.content" style="width: 100%; height: 100%" />
    </modalsNasaModal>
  </div>
</template>
<script>
export default {
  name: "NuxtComponent",
  data() {
    return {
      modal: {
        opened: false,
        content: null,
      },
    };
  },
  created() {
    this.$nuxt.$on("openModal", ($event) => this.setModal($event));
    this.$nuxt.$on("closeModal", ($event) => this.setModal($event));
  },
  methods: {
    setModal(e) {
      this.modal.content = e.content;
      this.modal.opened = e.state;
    },
  },
};
</script>
