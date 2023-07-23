<script setup>
     import { ref, reactive } from 'vue'
     const imageIndex = ref(0);


    const images = reactive([
    {
      thumb: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxlZGl0b3JpYWwtZmVlZHwxfHx8ZW58MHx8fHx8&auto=format&fit=crop&w=150&q=60",
      full: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
    },
    {
      thumb: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDZ8fHxlbnwwfHx8fHw%3D&auto=format&fit=crop&w=150&q=60",
      full: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
    },
    {
      thumb: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE4fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=150&q=60",
      full: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
    },
    {
      thumb: "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=150&q=40",
      full: "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
    }
  ]);

  function imageSlideRight(){
    imageIndex.value++;
    imageIndex.value = imageIndex.value;
    if(imageIndex.value == images.length){
      imageIndex.value = 0;
    }
  }

  function imageSlideLeft(){
    imageIndex.value--;
    imageIndex.value = imageIndex.value;
    if(imageIndex.value == -1){
      imageIndex.value = images.length-1;
    }
  }
</script>

<template>
  
  <section class="container">
    <h1 class="text-center text-2xl py-10">Image Carousel Project</h1><br><br>
    <div class="">
        <img class="shadow-sm"  v-for="(image,index) in images" :src="image.thumb" :key="index" style="height:100px; margin:2px;" :style="index==imageIndex?'filter: blur(3px)':''">
    </div><br>
    <div id="carouselExampleControls" class="carousel slide" data-ride="carousel">
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img :src="images[imageIndex].full" class="d-block w-100" alt="..." style="height:500px;">
      </div>
    </div>
   <button class="carousel-control-prev" type="button" @click="imageSlideLeft()">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="sr-only">Previous</span>
    </button>
    <button class="carousel-control-next" type="button"  @click="imageSlideRight()">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="sr-only">Next</span>
    </button>
  </div>
  </section>

</template>

<style scoped>

</style>
