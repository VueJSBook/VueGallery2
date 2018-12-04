<template>
  <div class="row">
    <div class="col-sm-8 col-12">
      <img :src="selectedImage.imageLink" class="img-fluid">
    </div>
    <div class="col-sm-4 col-12">
      <h1>{{selectedImage.title}}</h1>
      <p>{{selectedImage.description}}</p>
    </div>
  </div>
</template>

<script>
    export default {
        props: ['selectedImage']
    }
</script>