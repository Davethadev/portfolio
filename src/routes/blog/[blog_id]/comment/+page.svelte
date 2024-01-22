<script>
  import axios from "axios";
  import { Toasts } from "svoast";
  import { toast } from "svoast";
  import { onMount } from "svelte";
  import { page } from "$app/stores";
  import { goto } from "$app/navigation";

  import spinner from "../../../../assets/spinner.svg";

  let post;
  let loading;
  let submitting;

  let formData = {
    email: "",
    comment: "",
  };

  const url = $page.params.blog_id;

  const getBlogPost = async () => {
    loading = true;
    try {
      const response = await axios.get(
        "https://daveedzblog.glitch.me/api/v1/blog/" + url
      );
      post = response?.data?.blog;
    } catch (error) {
      toast.error("Unable to fetch blog post now. Please try again later");
    } finally {
      loading = false;
    }
  };

  const handlePost = async () => {
    submitting = true;
    try {
      const response = await axios.post(
        "https://daveedzblog.glitch.me/api/v1/blog/" + url + "/comment",
        formData
      );
      if (response?.data?.comment) {
        goto("/blog/" + url);
      }
    } catch (error) {
      toast.error("Please provide a reply");
    } finally {
      submitting = false;
    }
  };

  onMount(() => getBlogPost());
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
          <small>{post.createdAt.slice(0, 10)}</small>
          <h2 class="text-lg font-[500] py-[2px]">{post.title}</h2>
          <p class="text-base">{post.blog_post}</p>
        </article>
        <form action="" on:submit|preventDefault={handlePost}>
          <input
            bind:value={formData.email}
            type="text"
            class="bg-transparent w-full px-4 py-2 border-none outline-none focus:outline-none focus:border-none mt-4"
            placeholder="Please enter your email"
          />
          <textarea
            bind:value={formData.comment}
            name=""
            class="w-full h-56 resize-none my-4 bg-transparent border-none outline-none focus:outline-none focus:border-none px-4 py-4"
            placeholder="Post your reply"
          ></textarea>
          <button
            disabled={submitting}
            type="submit"
            class="bg-black text-white rounded w-48 py-2 px-4 flex justify-center items-center"
            >{#if submitting}
              <img src={spinner} alt="" />
            {:else}
              Post
            {/if}
          </button>
        </form>
      {/if}
    </div>
  </section>
</main>
