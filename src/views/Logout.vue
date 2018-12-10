<template>
</template>

<script>
    import { logout } from '../services/auth.js'

    export default {
        name: 'logout',
        created () {
            logout()
            this.$router.push('/')
        }
    }
</script>

<style scoped>
</style>