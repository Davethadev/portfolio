<script>
  import Icon from "@iconify/svelte";
  import { onMount } from "svelte";
  import { goto } from "$app/navigation";
  import { gsap } from "gsap/dist/gsap";
  import { MotionPathPlugin } from "gsap/dist/MotionPathPlugin";
  let isMobileNav = false;
  const openMobileNav = () => (isMobileNav = true);
  const closeMobileNav = () => (isMobileNav = false);

  let LogoElement;
  const timeline = gsap.timeline({
    defaults: { duration: 2, ease: "power4.inOut" },
  });

  onMount(() => {
    timeline.to(LogoElement, {
      "clip-path": "polygon(0% 100%, 100% 100%, 100% 0%, 0% 0%)",
      opacity: 1,
      y: 0,
    });
  });

  const navigateToWork = () => {
    closeMobileNav();
    goto("#work");
  };

  const navigateToAbout = () => {
    closeMobileNav();
    goto("#about");
  };

  const navigateToContact = () => {
    closeMobileNav();
    goto("#contact-me");
  };
</script>

<div
  class="w-full md:w-[85%] mx-auto my-0 flex justify-between items-center pt-8 px-4 md:px-0"
>
  <div
    bind:this={LogoElement}
    id="logo"
    class="font-[400] text-white text-base"
  >
    David Umanah
  </div>
  <button class="md:hidden" on:click={openMobileNav}>
    <Icon icon="mdi-light:menu" style="font-size: 28px; color: white;" />
  </button>
  <div class="hidden md:block">
    <!-- <a href="#">Articles</a> -->
    <a class="font-[400] text-[rgb(153,153,153)] text-lg ml-4" href="#work"
      >Work</a
    >
    <a class="font-[400] text-[#999999] text-lg ml-4" href="#about">About</a>
    <a class="font-[400] text-[#999999] text-lg ml-4" href="#contact-me"
      >Contact</a
    >
  </div>
  <a
    class="w-fit text-center font-[400] py-1 px-4 text-black bg-yellow-300 text-lg rounded hidden md:block"
    href="mailto: david_umanah@yahoo.com">Get in touch</a
  >
</div>
{#if isMobileNav}
  <div
    class="md:hidden w-full text-center py-8 px-0 absolute top-0 z-10 bg-black h-screen overflow-y-clip"
  >
    <button class="md:hidden" on:click={closeMobileNav}>
      <Icon
        icon="material-symbols-light:close"
        style="font-size: 28px; color: white; position: absolute; right: 16px;"
      />
    </button>
    <!-- <a href="#">Articles</a> -->
    <button
      on:click={navigateToWork}
      class="uppercase text-white mt-16 flex justify-center w-full">Work</button
    >
    <button
      on:click={navigateToAbout}
      class="uppercase text-white mt-4 flex justify-center w-full">About</button
    >
    <button
      on:click={navigateToContact}
      class="uppercase text-white mt-4 flex justify-center w-full"
      >Contact</button
    >
    <button
      class="w-fit mx-auto text-center font-[400] py-1 px-4 text-black bg-yellow-300 text-base rounded mt-4"
      href="mailto: david_umanah@yahoo.com">Get in touch</button
    >
  </div>
{/if}

<style lang="postcss">
  /* :global(html) {
    background-color: theme(colors.gray.100);
  } */

  #logo {
    clip-path: polygon(0 100%, 100% 100%, 100% 100%, 0% 100%);
    opacity: 0;
    transform: translateY(20px);
  }
</style>
