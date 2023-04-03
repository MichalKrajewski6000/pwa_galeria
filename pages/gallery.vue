<template>
  <div>
    <TopNav />
    <div class="gallery">
      <h1>Image Gallery</h1>
      <BigImage :image="this.img" />
      <SmallImage :images="items" @selectedImg="showImg($event)" />
    </div>
  </div>
</template>

<script>
import BigImage from "~/components/gallery/BigImage.vue";
import SmallImage from "~/components/gallery/SmallImage.vue";
import TopNav from "../components/nav/TopNav.vue";
export default {
  name: "GalleryPage",
  components: { TopNav, BigImage, SmallImage },

  data() {
    return {
      items: [
        "https://bpb-us-e1.wpmucdn.com/sites.nova.edu/dist/c/2/files/2018/09/Cayd-6-with-Colonel-245qkmg-768x432.jpg",
        "https://wallpapers.com/images/hd/cayde-6-hunter-vanguard-destiny-2-key-character-9u5oqe1diooba64c.jpg",
        "https://asset.vg247.com/destiny_2_cayde-6.jpg/BROK/resize/1920x1920%3E/format/jpg/quality/80/destiny_2_cayde-6.jpg",
        "https://i.ytimg.com/vi/Amp-oa55P9Y/maxresdefault.jpg",
      ],
      img: "https://i.ytimg.com/vi/Amp-oa55P9Y/maxresdefault.jpg",
    };
  },

  methods: {
    showImg(url) {
      console.log("Ten event");
      console.log(url);
      this.img = url;
    },
  },
};
</script>
<style scoped>
.gallery {
  width: 50vw;
}
</style>
