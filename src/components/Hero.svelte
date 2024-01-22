<script>
  import HeaderImage from "../assets/nicer-avatar.png";

  import { gsap } from "gsap/dist/gsap";

  import { MotionPathPlugin } from "gsap/dist/MotionPathPlugin";

  import { onMount } from "svelte";

  let HeaderImageElement;

  onMount(() => {
    gsap.to(HeaderImageElement, { x: 0, duration: 1, ease: "power1.in" });
  });
</script>

<div
  class="w-full md:w-[85%] my-0 mx-auto md:flex justify-between items-center pt-14 px-4 md:px-0"
>
  <div
    bind:this={HeaderImageElement}
    class="md:hidden transform -translate-x-full"
  >
    <img src={HeaderImage} alt="" />
  </div>
  <div class="w-full md:w-[60%]">
    <h1
      class="font-bold text-white text-2xl md:text-5xl leading-snug pt-12 md:pt-0"
    >
      Helping you build beautiful and interactive websites.
    </h1>
    <p class="font-[400] text-[#999999] pt-4 text-base md:text-xl">
      Frontend web-developer, with over 4+ months of working experience with
      frontend technolgies like HTML, CSS and Javascript
    </p>
  </div>
  <div class="hidden md:block">
    <img src={HeaderImage} alt="" />
  </div>
</div>
