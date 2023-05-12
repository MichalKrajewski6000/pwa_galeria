<template>
  <div>
    <!-- <TopNav /> -->
    <div class="gallery">
      <h1>Image Gallery</h1>
      <BigImage
        :image="bigImgUrl"
        :key="selectedImg"
        @click.native="showModal"
      />
      <SmallImage :images="items" @selectedImg="showImg($event)" />
    </div>
    <Modal
      v-if="modalVisible"
      :images="items"
      :mainImgId="selectedImg"
      :mainImgUrl="bigImgUrl"
      :mainImgAlt="bigImgAlt"
      @setActiveImg="showImg"
      @closeModal="closeModal"
    />
  </div>
</template>

<script>
import BigImage from "~/components/gallery/BigImage.vue";
import SmallImage from "~/components/gallery/SmallImage.vue";
import TopNav from "../components/nav/TopNav.vue";
import Modal from "~/components/modals/modal.vue";

export default {
  name: "GalleryPage",
  components: { TopNav, BigImage, SmallImage, Modal },

  data() {
    return {
      items: [
        {
          id: 1,
          url: "https://bpb-us-e1.wpmucdn.com/sites.nova.edu/dist/c/2/files/2018/09/Cayd-6-with-Colonel-245qkmg-768x432.jpg",
          alt: "cayde-1",
        },
        {
          id: 2,
          url: "https://wallpapers.com/images/hd/cayde-6-hunter-vanguard-destiny-2-key-character-9u5oqe1diooba64c.jpg",
          alt: "cayde-2",
        },
        {
          id: 3,
          url: "https://asset.vg247.com/destiny_2_cayde-6.jpg/BROK/resize/1920x1920%3E/format/jpg/quality/80/destiny_2_cayde-6.jpg",
          alt: "cayde-3",
        },
        {
          id: 4,
          url: "https://i.ytimg.com/vi/Amp-oa55P9Y/maxresdefault.jpg",
          alt: "cayde-4",
        },
      ],
      selectedImg: 1,
      modalVisible: false,
    };
  },

  computed: {
    bigImgUrl() {
      return this.items.find((img) => img.id === this.selectedImg).url;
    },
    bigImgAlt() {
      return this.items.find((img) => img.id === this.selectedImg).alt;
    },
  },

  methods: {
    showImg(id) {
      this.selectedImg = id;
    },
    showModal() {
      this.modalVisible = true;
    },
    closeModal() {
      this.modalVisible = false;
    },
  },
};
</script>
<style scoped>
.gallery {
  width: 50vw;
  align-items: center;
  justify-content: center;
  margin-left: 20vw;
}
</style>
