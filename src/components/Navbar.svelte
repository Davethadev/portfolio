<script>
  import Icon from "@iconify/svelte";

  let isMobileNavOpen = false;

  const openMobileNav = () => (isMobileNavOpen = true);
  const closeMobileNav = () => (isMobileNavOpen = false);
</script>

<div
  class="w-full md:w-[85%] mx-auto my-0 flex justify-between items-center pt-8 px-4 md:px-0"
>
  <div class="font-normal text-white text-base">David Umanah</div>
  <button class="md:hidden" on:click={openMobileNav}>
    <Icon icon="mdi-light:menu" style="font-size: 28px; color: white;" />
  </button>
  <div class="hidden md:block">
    <!-- <a href="#">Articles</a> -->
    <a class="font-normal text-[#999999] ml-4 text-lg" href="#work">Work</a>
    <a class="font-normal text-[#999999] ml-4 text-lg" href="#about">About</a>
    <a class="font-normal text-[#999999] ml-4 text-lg" href="#contact-me"
      >Contact</a
    >
  </div>
  <a
    class="w-fit text-center font-normal py-1 px-4 text-black bg-yellow-300 text-lg rounded hidden md:block"
    href="mailto: david_umanah@yahoo.com">Get in touch</a
  >
</div>
{#if isMobileNavOpen}
  <div
    class="md:hidden w-full text-center py-8 px-0 absolute top-0 z-10 bg-black h-screen"
  >
    <button class="md:hidden" on:click={closeMobileNav}>
      <Icon
        icon="material-symbols-light:close"
        style="font-size: 28px; color: white; position: absolute; right: 16px;"
      />
    </button>
    <!-- <a href="#">Articles</a> -->
    <a class="uppercase text-white mt-16 mb-4 block" href="#work">Work</a>
    <a class="uppercase text-white mb-4 block" href="#about">About</a>
    <a class="uppercase text-white mb-4 block" href="#contact-me">Contact</a>
    <a
      class="w-fit mx-auto text-center font-normal py-1 px-4 text-black bg-yellow-300 text-base rounded block"
      href="mailto: david_umanah@yahoo.com">Get in touch</a
    >
  </div>
{/if}

<style lang="postcss">
  /* :global(html) {
    background-color: theme(colors.gray.100);
  } */
</style>
