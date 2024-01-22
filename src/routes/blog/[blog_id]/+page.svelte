<script>
  import axios from "axios";
  import { Toasts } from "svoast";
  import { toast } from "svoast";
  import { onMount } from "svelte";
  import { page } from "$app/stores";
  import { goto } from "$app/navigation";
  let post;
  let comments;
  let url;
  let loading;

  const getBlogContent = async () => {
    url = $page.params.blog_id;
    loading = true;
    try {
      const response = await axios.get(
        "https://daveedzblog.glitch.me/api/v1/blog/" + url
      );
      post = response?.data?.blog;
      comments = response?.data?.comments;
      console.log(comments);
    } catch (error) {
      toast.error("Unable to fetch blog post now. Please try again later");
    } finally {
      loading = false;
    }
  };

  onMount(() => getBlogContent());

  const getCommentForm = () => {
    goto("/blog/" + url + "/comment");
  };
</script>

<main>
  <Toasts position="top-right" />
  <section class="w-full">
    <div class="w-full px-4 md:px-0 md:w-[55%] mx-auto">
      {#if loading}
        <div class="w-full flex justify-center items-center mt-40">
          <div class="loader"></div>
        </div>
        <!-- <p class="w-full h-screen flex justify-center items-center">
          Loading...
        </p> -->
      {:else if post}
        <article>
          <div class="py-8">
            <h2 class="text-3xl font-[500]">{post.title}</h2>
            <small class="text-gray-600">{post.createdAt.slice(0, 10)}</small>
          </div>
          <p class="text-base">{post.blog_post}</p>
        </article>
        <div class="pt-8 pb-2">
          <h2 class="text-lg font-[500]">Comments</h2>
          <button
            on:click={getCommentForm}
            class="flex items-center justify-center gap-2 border-2 border-black rounded-2xl w-56 mx-auto my-8"
            ><span class="text-2xl">+</span><span class="text-base font-[500]"
              >Add comment</span
            ></button
          >
          {#if comments.length === 0}
            <p class="text-base font-[500]">No comments yet</p>
          {:else if comments}
            <div class="grid grid-cols-1 gap-4 text-left">
              {#each comments as comment (comment._id)}
                <article>
                  <p class="font-[500]">{comment.email}</p>
                  <p class="text-sm text-gray-600 py-1">{comment.comment}</p>
                </article>
              {/each}
            </div>
          {/if}
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
