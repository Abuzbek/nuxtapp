<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" to="/">NUXT</a>
      <div class="collapse navbar-collapse">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <nuxt-link
              class="nav-link"
              no-prefetch
              exact-active-class="active"
              to="/"
              >Home</nuxt-link
            >
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link" active-class="active" to="/about"
              >About</nuxt-link
            >
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link" active-class="active" to="/users"
              >Users</nuxt-link
            >
          </li>
           <li class="nav-item" v-if="!hasToken">
            <nuxt-link class="nav-link" active-class="active" to="/login"
              >Login</nuxt-link
            >
          </li>
          <li class="nav-item" v-else>
            <a class="nav-link" @click.prevent="onLogout" href="#"
              >Logout</a
            >
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
<script>
export default {
  computed:{
    hasToken(){
      return this.$store.getters.hasToken
    }
  },
  methods:{
    onLogout(){
      this.$store.dispatch('logout')
      this.$router.push('/login')
    }
  }
}
</script>