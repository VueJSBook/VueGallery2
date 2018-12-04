<template>
  <div class="gallery container mt-4">
    <single-image :selectedImage="selectedImage"></single-image>
    <image-list v-bind:images="images" @emitImage="showImage"></image-list>
  </div>
</template>

<script>
    import ImageList from './ImageList'
    import SingleImage from './SingleImage'

    export default {
        name: 'gallery',
        components: {SingleImage, ImageList},
        data () {
            return {
                selectedImage: '',
                images: [
                    {id: 1, title: 'First image', description: 'First image description', thumbnail: 'https://vuejsbook.com/img/vuejs/img1.jpg', imageLink: 'https://vuejsbook.com/img/vuejs/img1-l.jpg'},
                    {id: 2, title: 'Second image', description: 'Second image description', thumbnail: 'https://vuejsbook.com/img/vuejs/img2.jpg', imageLink: 'https://vuejsbook.com/img/vuejs/img2-l.jpg'},
                    {id: 3, title: 'Third image', description: 'Third image description', thumbnail: 'https://vuejsbook.com/img/vuejs/img3.jpg', imageLink: 'https://vuejsbook.com/img/vuejs/img3-l.jpg'},
                    {id: 4, title: 'Fourth image', description: 'Fourth image description', thumbnail: 'https://vuejsbook.com/img/vuejs/img4.jpg', imageLink: 'https://vuejsbook.com/img/vuejs/img4-l.jpg'},
                    {id: 5, title: 'Fifth image', description: 'Fifth image description', thumbnail: 'https://vuejsbook.com/img/vuejs/img5.jpg', imageLink: 'https://vuejsbook.com/img/vuejs/img5-l.jpg'},
                    {id: 6, title: 'Sixth image', description: 'Sixth image description', thumbnail: 'https://vuejsbook.com/img/vuejs/img6.jpg', imageLink: 'https://vuejsbook.com/img/vuejs/img6-l.jpg'},
                    {id: 7, title: 'Seventh image', description: 'Seventh image description', thumbnail: 'https://vuejsbook.com/img/vuejs/img7.jpg', imageLink: 'https://vuejsbook.com/img/vuejs/img7-l.jpg'},
                    {id: 8, title: 'Eight image', description: 'Eighth image description', thumbnail: 'https://vuejsbook.com/img/vuejs/img8.jpg', imageLink: 'https://vuejsbook.com/img/vuejs/img8-l.jpg'}
                ]
            }
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