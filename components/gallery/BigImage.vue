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
}
</style>