<template>
  <div class="hello">
<ul class="list-unstyled">
  <li class="media">
    <img src="http://www.w3.org/2000/svg" class="mr-3" alt="...">
    <div class="media-body">
      <h5 class="mt-0 mb-1">List-based media object</h5>
      Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.
    </div>
  </li>
</ul>
  </div>
</template>

<script>
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
    }
  }
};
</script>

</style>
