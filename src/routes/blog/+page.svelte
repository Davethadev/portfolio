<script>
  import axios from "axios";
  import { onMount } from "svelte";
  import { Toasts } from "svoast";
  import { toast } from "svoast";
  let blogPosts;
  let loading;

  const getBlogPosts = async () => {
    loading = true;
    try {
      const response = await axios.get(
        "https://daveedzblog.glitch.me/api/v1/blog"
      );
      if (response?.data?.posts) {
        blogPosts = response?.data?.posts;
      }
    } catch (error) {
      toast.error("Unable to fetch blog posts now. Please try again later");
    } finally {
      loading = false;
    }
  };

  onMount(() => {
    getBlogPosts();
  });
</script>

<main>
  <Toasts position="top-right" />
  <section class="w-full">
    <h1 class="text-2xl font-bold text-center py-8">My Blog posts</h1>
    <div class="w-[85%] mx-auto py-4">
      {#if loading}
        <div class="w-full flex justify-center items-center mt-40">
          <div class="loader"></div>
        </div>
        <!-- <p class="w-full h-screen flex justify-center items-center">
          Loading...
        </p> -->
      {:else if blogPosts && blogPosts.length === 0}
        <p class="text-base font-[500] text-center mt-40">
          No blog posts yet😥
        </p>
      {:else if blogPosts}
        <div class="grid grid-cols-1 gap-4">
          {#each blogPosts as post (post._id)}
            <article>
              <small class="text-gray-600">{post.createdAt.slice(0, 10)}</small>
              <h1 class="font-[500] text-base">
                {post.title}
              </h1>
              <p class="text-sm py-[2px]">{post.blog_post}</p>
              <a class="hover:underline text-sm" href="/blog/{post._id}"
                >View full post</a
              >
            </article>
          {/each}
        </div>
      {/if}
    </div>
  </section>
</main>

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.gray.100);
  }
</style>
