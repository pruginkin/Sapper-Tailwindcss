<script context="module">
  export function preload({ params, query }) {
    return this.fetch(`blog.json`)
      .then(r => r.json())
      .then(posts => {
        return { posts };
      });
  }
</script>

<script>
  export let posts;
</script>

<svelte:head>
  <title>Blog</title>
</svelte:head>

<div class="container mx-auto">
  <h1 class="my-5">Recent posts</h1>

  <ul>
    {#each posts as post}
      <li class="my-1">
        <a rel="prefetch" href="blog/{post.slug}">{post.title}</a>
      </li>
    {/each}
  </ul>
</div>
