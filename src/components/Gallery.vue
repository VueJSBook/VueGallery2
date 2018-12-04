<template>
  <div class="gallery container mt-4">
    <single-image :selectedImage="selectedImage"></single-image>
    <image-list v-bind:images="images" @emitImage="showImage"></image-list>
  </div>
</template>

<script>
    import ImageList from './ImageList'
    import SingleImage from './SingleImage'
    import axios from 'axios'

    export default {
        name: 'gallery',
        components: {SingleImage, ImageList},
        data () {
            return {
                selectedImage: '',
                images: [],
                errors: []
            }
        },
        created () {
            axios.get('http://vuejsbook.test/api/v1/images')
                .then(response => {
                    this.images = response.data
                })
                .catch(e => {
                    this.errors.push(e)
                })
        },
        methods: {
            showImage: function (image) {
                this.selectedImage = image
            }
        }
    }
</script>

<style>
  img {
    -webkit-box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.2);
    -moz-box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.2);
    box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.2);
    margin-bottom:20px;
  }

  img:hover {
    filter: gray; /* IE6-9 */
    -webkit-filter: grayscale(1); /* Google Chrome, Safari 6+ & Opera 15+ */
  }
</style>