<template>
  <h1 class="text-green-900">hello gemography</h1>
</template>

<script>
  import axios from 'axios'

  export default {

    created() {
      this.getRepos()
    },

    data() {
      return {
        repos: {}
      }
    },

    methods: {
      getRepos() {
        axios.get('https://api.github.com/search/repositories?q=created:>2017-10-22&sort=stars&order=desc')
          .then((res) => console.log(res.data.items))
          .catch( (error) => console.log(error))
      }
    }
  }

</script>

<style>

</style>
