<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="#">{{ brand }}</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav ml-auto">
        <li class="nav-item active">
          <router-link to="/" class="nav-link">Home</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/about" class="nav-link">About</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/contact" class="nav-link">Contact</router-link>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            Member
          </a>
          <div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbarDropdown" >
            <router-link v-show="!isLoggedIn" to="/register" class="dropdown-item">Register</router-link>
            <router-link v-show="!isLoggedIn" to="/login" class="dropdown-item">Login</router-link>
            <router-link v-show="isLoggedIn" to="/admin" class="dropdown-item">Admin</router-link>
            <router-link v-show="isLoggedIn" to="/logout" class="dropdown-item">Logout</router-link>
          </div>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
    import { loggedIn } from '../services/auth.js'
    import { EventBus } from '../services/event-bus.js'
    export default {
        data () {
            return {
                brand: 'Vue.js Book',
                isLoggedIn: loggedIn()
            }
        },
        created () {
            EventBus.$on('login', () => {
                this.isLoggedIn = loggedIn()
            })
            EventBus.$on('logout', () => {
                this.isLoggedIn = loggedIn()
            })
        }
    }
</script>