<template>
  <div class="hello" mt-3>
    <ul class="list-unstyled">
      <li class="media m-3" v-for="post in posts">

        <img :src="post.data.thumbnail" class="mr-3" alt="Generic Placeholder Image">
        <div class="media-body">
          <h5 class="mt-0 mb-1">{{post.data.title}}</h5>
          <p>
            <h3 class="text-danger">{{post.data.ups}} ⬆️</h3>
            <p>created {{formatDate(post.data.created_utc)}} ago</p>
            <span class="badge badge-secondary">{{post.data.num_comments}} comments</span>
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import { parse, formatDistanceToNow, formatDistance } from "date-fns";

export default {
  name: "Posts",
  data() {
    return {
      posts: []
    };
  },
  mounted() {
    this.load();
  },
  methods: {
    load() {
      const url = "https://www.reddit.com/r/MovieDetails/.json";
      fetch(url)
        .then(response => response.json())
        .then(result => {
          this.posts = result.data.children;
        });
    },
    formatDate(date) {
      return formatDistanceToNow(date * 1000);
    }
  }
};
</script>
<style>
</style>

