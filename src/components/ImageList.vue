<template>
  <div>
    <div class="row">
      <div v-for="image in images" :key="image.id" class="col-md-3 col-sm-4 col-6"><a href="#" @click="emitImage(image)"><img class="img-fluid" v-bind:src="image.thumbnail" /></a></div>
    </div>
  </div>
</template>

<script>
    export default {
        props: ['images'],
        methods: {
            emitImage: function (image) {
                this.$emit('emitImage', image)
            }
        }
    }
</script>