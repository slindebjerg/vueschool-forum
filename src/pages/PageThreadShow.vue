<template>
  <div class="col-large push-top">
    <h1>{{thread.title}}</h1>
    <PostList :posts="posts"/>
    <form v-on:submit.prevent="addPost">
      <div class="form-group">
        <textarea
        name=""
        id=""
        cols="30"
        rows="10"
        class="form-input"
        :value="newPostText"
        @input="newPostText = $event.target.value"
        ></textarea>
      </div>
      <div class="form-actions">
        <button class="btn-blue">Submit post</button>
      </div>
    </form>
  </div>
</template>

<script>
  import sourceData from '@/data'
  import PostList from '@/components/PostList'
  export default {

    components: {
      PostList
    },

    props: {
      id: {
        required: true,
        type: String
      }
    },

    data () {
      return {
        thread: sourceData.threads[this.id],
        newPostText: ''
      }
    },

    computed: {
      posts () {
        const postIds = Object.values(this.thread.posts)
        return Object.values(sourceData.posts)
          .filter(post => postIds.includes(post['.key']))
      }
    },

    methods: {
      addPost () {
        const postId = 'greatPost' + Math.random()
        const post = {
          text: this.newPostText,
          publishedAt: Math.floor(Date.now() / 1000),
          threadId: this.id,
          userId: 'Miej9zSGMRZKDvMXzfxjVOyv3RF3',
          '.key': postId
        }
        this.$set(sourceData.posts, postId, post)
        this.$set(this.thread.posts, postId, postId)
        this.$set(sourceData.users[post.userId].posts, postId, postId)
        this.newPostText = ''
      }
    }
  }
</script>