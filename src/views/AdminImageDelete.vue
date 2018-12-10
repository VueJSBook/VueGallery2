<template>
  <div class="container adminimagedelete">
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
            <h5 class="float-left">Are you sure that you want to delete {{ image.title }}?</h5>
            <div class="clearfix"></div>
          </div>
          <div class="card-body mt-2">
            <form @submit.prevent="deleteImage">
              <div class="row">
                <div class="col-lg-12">
                  <router-link to="/admin/" class="btn btn-default">Cancel</router-link>
                  <button type="submit" class="btn btn-primary">Delete</button>
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
        name: 'adminimagedelete',
        data () {
            return {
                errors: [],
                image: []
            }
        },
        created () {
            this.getImage(this.$route.params.id)
        },
        methods: {
            getImage: function (id) {
                axios.get('http://vuejsbook.test/api/v1/images/' + id)
                    .then(response => {
                        console.log(response.data)
                        this.image = response.data
                    })
                    .catch(e => {
                        this.errors.push(e)
                    })
            },
            deleteImage: function () {
                var config = {
                    headers: getAuthHeader()
                }
                const url = 'http://vuejsbook.test/api/v1/images/' + this.$route.params.id
                axios.delete(url, config)
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