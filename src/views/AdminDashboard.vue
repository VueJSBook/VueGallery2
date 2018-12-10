<template>
  <div class="container">
    <div class="row banner">
      <div class="col-md-12 mt-5">
        <div class="list-group">
          <div class="list-group-item">
            <div class="row-content">
              <h5><i class="far fa-grin-tongue mb-3"></i> Manage User</h5>
              <router-link to="/admin/users" class="btn btn-warning">All Users</router-link>
              <router-link to="/admin/users/create" class="btn btn-success">New User</router-link>
            </div>
          </div>
          <div class="list-group-separator"></div>
          <div class="list-group-item">
            <div class="row-content">
              <h5><i class="fas fa-file-signature mb-3"></i> Manage Images</h5>
              <router-link to="/admin/images" class="btn btn-info">All Images</router-link>
              <router-link to="/admin/images/create" class="btn btn-success">New Image</router-link>
            </div>
          </div>
          <div class="list-group-separator"></div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
    export default {
        name: 'admindashboard',
    }
</script>

<style scoped>
</style>