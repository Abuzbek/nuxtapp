<template>
  <div>
    <h1>{{pageTitle}}</h1>
    <ul>
      <li v-for="n of users" :key="n.id">
        <a href="#" @click.prevent="openUser(n)">
          {{n.name}}
        </a>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data:()=>({
    pageTitle:'Users page'
  }),
  middleware:['auth'],
  async fetch({store}){
    if(store.getters['users/users'].length == 0){
      await store.dispatch('users/fetch')
    }
  },
  computed:{
    users(){
      return this.$store.getters['users/users']
    }
  },
  methods:{
    openUser(n){
      this.$router.push('/users/'+n.id)
    }
  },
}
</script>