<template>
  <div class="container adminimagecreate">
    <div class="row mb-4">
      <div class="col-md-12">
        <div>
          <router-link to="/admin/" class="btn btn-default"> Back</router-link>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-md-12">
      <div class="card">
        <div class="card-header ">
          <h5 class="float-left">Add a new image: {{ image.title }}</h5>
          <div class="clearfix"></div>
        </div>
        <div class="card-body mt-2">
          <form @submit.prevent="validateForm">
              <div class="form-group">
                <label for="thumbnail" class="col-lg-2 control-label">Thumbnail</label>
                <div class="col-lg-12">
                  <input v-validate="'required'" type="text" class="form-control" id="thumbnail" name="thumbnail" placeholder="Thumbnail of the image" v-model="image.thumbnail">
                  <span v-show="ferrors.has('thumbnail')" class="text-danger">{{ ferrors.first('thumbnail') }}</span>
                </div>
              </div>
              <div class="form-group">
                <label for="imagelink" class="col-lg-2 control-label">Image Link</label>
                <div class="col-lg-12">
                  <input v-validate="'required'" type="text" class="form-control" id="imageLink" name="imageLink" placeholder="Link of the image" v-model="image.imageLink">
                  <span v-show="ferrors.has('imageLink')" class="text-danger">{{ ferrors.first('imageLink') }}</span>
                </div>
              </div>
              <div class="form-group">
                <label for="title" class="col-lg-2 control-label">Title</label>
                <div class="col-lg-12">
                  <input v-validate="'required'" type="text" class="form-control" id="title" name="title" placeholder="Title" v-model="image.title">
                  <span v-show="ferrors.has('title')" class="text-danger">{{ ferrors.first('title') }}</span>
                </div>
              </div>
              <div class="form-group">
                <label for="description" class="col-lg-2 control-label">Description</label>
                <div class="col-lg-12">
                  <textarea v-validate="'required'" class="form-control" rows="3" id="description" name="description" placeholder="Description of the image" v-model="image.description"></textarea>
                  <span v-show="ferrors.has('description')" class="text-danger">{{ ferrors.first('description') }}</span>
                </div>
              </div>

              <div class="form-group">
                <div class="col-lg-12 col-lg-offset-2">
                  <router-link to="/admin/" class="btn btn-default">Cancel</router-link>
                  <button type="submit" class="btn btn-primary">Create</button>
                </div>
              </div>
          </form>
        </div>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
    import axios from 'axios'
    import { getAuthHeader } from '../services/auth.js'

    export default {
        name: 'adminimagecreate',
        data () {
            return {
                errors: [],
                image: {
                    thumbnail: '',
                    imageLink: '',
                    title: '',
                    description: ''
                }
            }
        },
        methods: {
            validateForm (e) {
                this.$validator.validateAll()
                if (!this.ferrors.any()) {
                    this.createImage()
                }
            },
            createImage: function () {
                var config = {
                    headers: getAuthHeader()
                }
                axios.post('http://vuejsbook.test/api/v1/images', this.image, config)
                    .then(response => {
                        console.log(response.data)
                        this.$router.push('/admin/images')
                    })
                    .catch(e => {
                        this.errors.push(e)
                    })
            }
        }
    }
</script>

<style scoped>
</style>