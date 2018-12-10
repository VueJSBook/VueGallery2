<template>
  <div class="container register">
    <div class="row mb-4">
      <div class="col-md-12">
        <div>
          <router-link to="/admin/" class="btn btn-default"> Back</router-link>
        </div>
      </div>
    </div>

    <div class="row">
      <div class="col-md-12">
        <div v-if="status=='success'" class="alert alert-success" role="alert"> {{ message }} </div>
        <div v-if="status=='error'">
          <div v-for="error in errors">
            <div class="alert alert-danger" role="alert"> {{ error }} </div>
          </div>
        </div>
      </div>
    </div>

    <div class="row">
      <div class="col-md-12">
        <div class="card">
            <div class="card-header ">
              <h5 class="float-left">Register</h5>
              <div class="clearfix"></div>
            </div>
            <div class="card-body mt-2">
              <form @submit.prevent="validateForm">
                <div class="form-group">
                  <label for="email" class="col-lg-12 control-label">Email</label>
                  <div class="col-lg-12">
                    <input v-validate="'required|email'" type="text" class="form-control" id="email" name="email" placeholder="Enter your email" v-model="user.email">
                    <span v-show="ferrors.has('email')" class="text-danger">{{ ferrors.first('email') }}</span>
                  </div>
                </div>
                <div class="form-group">
                  <label for="name" class="col-lg-12 control-label">Full name</label>
                  <div class="col-lg-12">
                    <input v-validate="'required'" type="text" class="form-control" id="name" name="name" placeholder="Enter your name" v-model="user.name">
                    <span v-show="ferrors.has('name')" class="text-danger">{{ ferrors.first('name') }}</span>
                  </div>
                </div>
                <div class="form-group">
                  <label for="password" class="col-lg-12 control-label">Password</label>
                  <div class="col-lg-12">
                    <input v-validate="'required'" ref="password" type="password" class="form-control" id="password" name="password" placeholder="Password" v-model="user.password">
                    <span v-show="ferrors.has('password')" class="text-danger">{{ ferrors.first('password') }}</span>
                  </div>
                </div>
                <div class="form-group">
                  <label for="password_confirmation" class="col-lg-12 control-label">Password Confirmation</label>
                  <div class="col-lg-12">
                    <input v-validate="'required|confirmed:password'"  type="password" class="form-control" id="password_confirmation" name="password_confirmation" placeholder="Password Confirmation" v-model="user.password_confirmation">
                    <span v-show="ferrors.has('password_confirmation')" class="text-danger">{{ ferrors.first('password_confirmation') }}</span>
                  </div>
                </div>
                <div class="form-group">
                  <div class="col-lg-12">
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
    import auth from '../services/auth.js'

    export default {
        name: 'register',
        data () {
            return {
                errors: [],
                user: {
                    email: '',
                    name: '',
                    password: '',
                    password_confirmation: ''
                },
                status: '',
                message: ''
            }
        },
        methods: {
            validateForm (e) {
                this.$validator.validateAll()
                if (!this.ferrors.any()) {
                    auth.signup(this, this.user)
                }
            }
        }
    }
</script>

<style scoped>
</style>