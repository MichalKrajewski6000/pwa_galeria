<template>
  <div class="modal">
    <div class="modal-content">
      <div class="modal-header">
        <div>Gallery</div>
        <div class="close-btn" @click="closeModal">
          <Icon icon="mdi:close-thick" width="25" height="25" />
        </div>
      </div>
      <div class="modal-wrapper">
        <div class="small-img-container">
          <SmallImage 
          :images="images"
          :class="setActiveClass(mainImgId)"
          @setActiveImg="setActiveImg" />
        </div>
        <div :class="setPrevImgClass" @click="selectPrevImg">
          <Icon icon="mdi:triangle" width="25" height="25" :rotate="3" />
        </div>
        <div class="main-img">
          <img :src="mainImgUrl" :alt="mainImgAlt" />
        </div>
        <div :class="setNextImgClass" @click="selectNextImg">
          <Icon icon="mdi:triangle" width="25" height="25" :rotate="1" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SmallImage from '../gallery/SmallImage.vue';
import { Icon } from '@iconify/vue2';

export default {
  components: { Icon, SmallImage },
  name: "Modal",

  props: {
    images: {
      type: Array,
      required: true
    },
    mainImgId: {
      type: Number,
      required: true,
    },
    mainImgUrl: {
      type: String,
      required: true,
    },
    mainImgAlt: {
      type: String,
      required: true,
    }
  },

  methods: {
    setActiveImg(id) {
      this.$emit("setActiveImg", id);
    },

    setActiveClass(id) {
      return id === this.mainImgId ? "active-thumb" : "";
    },

    selectPrevImg() {
      const imgId = this.mainImgId !== 1 ? this.mainImgId - 1 : 1;
      this.$emit("setActiveImg", imgId);
    },

    selectNextImg() {
      const imgId = this.mainImgId < this.images.length ? this.mainImgId + 1 : this.images.length;
      this.$emit("setActiveImg", imgId);
    },

    closeModal() {
      this.$emit("closeModal");
    }
  },

  computed: {
    setPrevImgClass() {
      return this.mainImgId === 1 ? "change-img-btn-disabled" : "change-img-btn";
    },

    setNextImgClass() {
      return this.mainImgId === this.images.length ? "change-img-btn-disabled" : "change-img-btn";
    },
  }
};
</script>
<style scoped>
.modal {
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  padding: 0;
  margin: 0;
  overflow: auto;
  left: 0;
  top: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.7);
}

.modal-content {
  background-color: white;
  width: 80%;
  margin: 0;
  padding: 0;
  align-items: center;
  border-radius: 0.25rem;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}

.modal-header {
  margin: 0;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-content: center;
  font-size: 1.5em;
  background-color: gray;
  border-top-left-radius: 0.25em;
  border-top-right-radius: 0.25em;
}

.modal-wrapper {
  margin: 0;
  padding: 1em;
  width: 100%;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  column-gap: 1em;
}

.small-img-container {
  margin: 0;
  padding: 0;
  width: 20vw;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: flex-start;
  gap: 1em;
}

.main-img {
  margin: 0;
  padding: 0;
  width: 50vw;
  display: flex;
  justify-content: center;
  align-items: center;
  object-fit: contain;
}

img.main-img {
  width: 100%;
  height: 100%;
}

.active-thumb {
  border: 1px solid darkgray;
  border-radius: 10px;
}

.change-img-btn, .close-btn {
  margin: 0;
  padding: 0;
  border-radius: 50%;
}

.change-img-btn-disabled {
  color: gray;
  background-color: silver;
}

.change-img-btn:hover {
  color: blue;
  cursor: pointer;
}

.close-btn:hover {
  color: white;
  background-color: gray;
  cursor: pointer;
  border-radius: 50%;
}
</style>
