<template>
  <section>
    <div v-if="$route.query.message" class="alert alert-danger">
      Need login first
    </div>
    <h1>Login Page</h1>
    <form @submit.prevent="onSubmit">
      <div class="form-group">
        <input v-model="input" type="text" class="form-control" />
      </div>
      <p>
        <nuxt-link to="/">To home page</nuxt-link>
      </p>

      <button :disabled="disabledBtn" class="btn btn-success">Submit</button>
    </form>
  </section>
</template>
<script>
export default {
  layout:'empty',
  data:()=>({
    input:''
  }),
  computed:{
    disabledBtn(){
      console.log(this.input);
    }
  },
  methods:{
    onSubmit(){
      this.$store.dispatch('login')
      this.$router.push('/')
    },
  }
}
</script>
<style scoped>
form {
  width: 500px;
}
</style>
