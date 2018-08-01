<template>
  <div class="posts">
    <div class="loading" v-if="isLoading">
      <img src="../assets/loading.gif" alt="">
    </div>
    <div class="post-list">
      <ul>
        <li v-for="post in posts" :key="post.id">
          <img :src="post.author.avatar_url" alt="">
          <span class="count">
            <span class="reply-count">{{post.reply_count}}</span>/<span class="visit-count">{{post.visit_count}}</span>
          </span>
          <div class="message">
            <p>{{post.title}}</p>
            <span>{{post.last_reply_at | timeFilter}}</span>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name : 'PostList',
  data() {
    return {
      isLoading: true,
      posts: []
    }
  },
  methods: {
    getData() {
      this.$axios.get('https://cnodejs.org/api/v1/topics', {
        params: {
          limit: 20,
          page: 1
        }
      })
        .then((res) => {
          this.posts = res.data.data
          this.isLoading = false
        })
        .catch((err) => {console.log(err)})
    }
  },
  beforeMount() {
    this.getData()
  }
}
</script>

<style scoped>
.posts{width: 84%; margin: 0 auto; background: #FFFFFF;}
.post-list ul li{height: 50px; border-bottom: 1px solid #F0F0F0; display: flex; flex-direction: row; align-items: center;}
.post-list ul li img{height: 65%; border-radius: 3px; margin-left: 1%;}
.post-list ul li .count{display: flex; justify-content: center; align-items: center; width: 8%;}
.post-list ul li .reply-count{font-size: 14px;}
.post-list ul li .visit-count{font-size: 12px; color: #B8B8B8;}
.post-list ul li .message{width: 100%; display: flex; flex-direction: row; justify-content: space-between;}
.post-list ul li .message>span{font-size: 14px; color: #B8B8B8;}
</style>
