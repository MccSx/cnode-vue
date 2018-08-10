<template>
 <div class="post-item">
  article
 </div>
</template>

<script>
export default {
  name : 'articleConponent',
  data() {
    return {
      articleData: {}
    }
  },
  components: {

  },
  created() {
    this.getArticleData()
  },
  methods: {
    getArticleData() {
      this.$axios.get(`https://cnodejs.org/api/v1/topic/${this.$route.params.userId}`)
      .then( res => {
        this.articleData = res.data.data
        console.log(res.data.data)
      })
      .catch( err => {
        console.log(err)
      })
    }
  }
}
</script>

<style scoped>
</style>
