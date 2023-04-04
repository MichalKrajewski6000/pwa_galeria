<template>
    <div>
         <img class="img" :src="image" />
    </div>
   
</template>
<script>
export default {
    name: 'BigImage',
    props: {
        image: {
            type: String,
            default: () => ''
        }
    },
    data() {
        return {
            
        }
    },

    created (){
        console.log(this.image)
    }
  }
</script>
<style scoped>
.img {
    width: 100%;
    transition: transform 0.5s ease;
}

.img:hover {
    transform: scale(1.1);
    margin: 1em;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    cursor: pointer;
}
</style>