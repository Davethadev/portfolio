<script>
  import HeaderImage from "../assets/nicer-avatar.png";
  import Chirp from "../assets/chirp-page.png";
  import LoopStudios from "../assets/loopstudios-landing-page.png";
  import EasyBank from "../assets/easybank-landing-page.png";
  import Insure from "../assets/insure-landing-page.png";
  import { onMount } from "svelte";
  import { MotionPathPlugin } from "gsap/dist/MotionPathPlugin";
  // import { goto } from "$app/navigation";
  import Icon from "@iconify/svelte";
  import { gsap } from "gsap/dist/gsap";
  // import Lenis from "@studio-freight/lenis";
  import { ScrollTrigger } from "gsap/dist/ScrollTrigger";
  import axios from "axios";

  let isMobileNav = false;
  const openMobileNav = () => (isMobileNav = true);
  const closeMobileNav = () => (isMobileNav = false);

  let HeaderImageElement;
  let HeaderImageElement2;
  let LogoElement;
  let MenuElement;
  let HeaderTextElement;
  let HeaderSubTextElement;
  let ProjectsHeaderElement;
  let AnimatedCard;
  let Link1;
  let Link2;
  let Link3;
  let Link4;
  let Button;
  let AnimatedCard1;
  let AnimatedCard2;
  let AnimatedCard3;
  let AnimatedCard4;

  onMount(() => {
    gsap.registerPlugin(ScrollTrigger);
    let timeline = gsap.timeline({
      defaults: { duration: 0.85, ease: "power2.inOut" },
    });
    // const lenis = new Lenis();

    // lenis.on("scroll", (e) => {
    //   console.log(e);
    // });

    // function raf(time) {
    //   lenis.raf(time);
    //   requestAnimationFrame(raf);
    // }

    // requestAnimationFrame(raf);

    timeline
      .to(LogoElement, {
        "clip-path": "polygon(0% 100%, 100% 100%, 100% 0%, 0% 0%)",
        opacity: 1,
        y: 0,
      })
      .to(Link1, { opacity: 1 })
      .to(Link2, { opacity: 1 })
      .to(Link3, { opacity: 1 })
      .to(Link4, { opacity: 1 })
      .to(Button, { x: 0 })
      .to(MenuElement, { opacity: 1 }, "-=3.5")
      .to(HeaderImageElement, { x: 0 }, "-=3.25")
      .to(
        HeaderTextElement,
        {
          "clip-path": "polygon(0% 100%, 100% 100%, 100% 0%, 0% 0%)",
          opacity: 1,
          y: 0,
        },
        "-=1"
      )
      .to(
        HeaderSubTextElement,
        {
          "clip-path": "polygon(0% 100%, 100% 100%, 100% 0%, 0% 0%)",
          opacity: 1,
          y: 0,
        },
        "-=1"
      )
      .to(HeaderImageElement2, { x: 0 })
      .to(ProjectsHeaderElement, { opacity: 1 }, "-=1")
      .to(AnimatedCard1, { scrollTrigger: AnimatedCard1, x: 0 })
      .to({ scrollTrigger: AnimatedCard2, x: 0 })
      .to({ scrollTrigger: AnimatedCard3, x: 0 })
      .to({ scrollTrigger: AnimatedCard4, x: 0 });
  });

  // const navigateToWork = () => {
  //   closeMobileNav();
  //   goto("#work");
  // };

  // const navigateToAbout = () => {
  //   closeMobileNav();
  //   goto("#about");
  // };

  // const navigateToContact = () => {
  //   closeMobileNav();
  //   goto("#contact-me");
  // };
</script>

<main>
  <div class="h-screen overflow-x-hidden">
    <div
      class="w-full md:w-[85%] mx-auto my-0 flex justify-between items-center pt-8 px-4 md:px-0"
    >
      <div
        bind:this={LogoElement}
        id="logo"
        class="font-[400] text-white text-base md:text-lg"
      >
        David Umanah
      </div>
      <button
        bind:this={MenuElement}
        class="md:hidden opacity-0"
        on:click={openMobileNav}
      >
        <Icon icon="mdi-light:menu" style="font-size: 28px; color: white;" />
      </button>
      <div class="hidden md:flex gap-4 overflow-x-hidden">
        <!-- <a href="#">Articles</a> -->
        <a
          bind:this={Link1}
          class="font-[400] text-[rgb(153,153,153)] text-lg opacity-0"
          href="#work">Work</a
        >
        <a
          bind:this={Link2}
          class="font-[400] text-[#999999] text-lg opacity-0"
          href="#about">About</a
        >
        <a
          bind:this={Link3}
          class="font-[400] text-[#999999] text-lg opacity-0"
          href="#contact-me">Contact</a
        >
        <a
          bind:this={Link4}
          class="font-[400] text-[#999999] text-lg opacity-0"
          href="/blog">Blog</a
        >
      </div>
      <a
        bind:this={Button}
        class="w-fit text-center font-[400] py-1 px-4 text-black bg-yellow-300 text-lg rounded hidden md:block translate-x-[100vw]"
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
        <button class="uppercase text-white mt-16 flex justify-center w-full"
          >Work</button
        >
        <button class="uppercase text-white mt-4 flex justify-center w-full"
          >About</button
        >
        <button class="uppercase text-white mt-4 flex justify-center w-full"
          >Contact</button
        >
        <a
          class="uppercase text-white mt-4 flex justify-center w-full"
          href="/blog">Blog</a
        >
        <button
          class="w-fit mx-auto text-center font-[400] py-1 px-4 text-black bg-yellow-300 text-base rounded mt-4"
          href="mailto: david_umanah@yahoo.com">Get in touch</button
        >
      </div>
    {/if}
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
          bind:this={HeaderTextElement}
          id="header-text"
          class="font-bold text-white text-2xl md:text-5xl leading-snug pt-12 md:pt-0"
        >
          Helping you build beautiful and interactive websites.
        </h1>
        <p
          bind:this={HeaderSubTextElement}
          id="header-subtext"
          class="font-[400] text-[#999999] pt-4 text-base md:text-xl"
        >
          Frontend web-developer, with over 4+ months of working experience with
          frontend technolgies like HTML, CSS and Javascript
        </p>
      </div>
      <div
        bind:this={HeaderImageElement2}
        class="hidden md:block translate-x-[100vw]"
      >
        <img src={HeaderImage} alt="" />
      </div>
    </div>
  </div>
  <div id="work" class="pb-14 px-0 pt-8">
    <h2
      bind:this={ProjectsHeaderElement}
      class="text-center font-[400] text-2xl md:text-4xl text-white py-16 opacity-0"
    >
      These are some of my projects
    </h2>
    <div
      class="w-full md:w-[85%] my-0 mx-auto grid grid-cols-1 md:grid-cols-2 gap-8 px-4 md:px-0"
    >
      <div bind:this={AnimatedCard1} class="">
        <img src={EasyBank} alt="" />
        <a
          class="block font-[400] text-white text-xl md:text-2xl py-2"
          href="https://davethadev.github.io/easybank-landing-page/"
          >Easybank landing page</a
        >
        <p class="font-[400] text-[#999999] px-0 pb-14 text-base md:text-lg">
          A landing page design from <a
            class="text-base md:text-lg text-white"
            href="https://www.frontendmentor.io/challenges/easybank-landing-page-WaUhkoDN"
            >frontendmentor</a
          > for a website that lets you manage your finances online as well as budget,
          save, invest and much more.
        </p>
      </div>
      <div bind:this={AnimatedCard2}>
        <img src={LoopStudios} alt="" />
        <a
          class="block font-[400] text-white text-xl md:text-2xl py-2"
          href="https://davethadev.github.io/loopstudios-landing-page/"
          >Loopstudios landing page</a
        >
        <p class="font-[400] text-[#999999] px-0 pb-14 text-base md:text-lg">
          Another design from <a
            class="text-base md:text-lg text-white"
            href="https://www.frontendmentor.io/challenges/loopstudios-landing-page-N88J5Onjw"
            >frontendmentor</a
          > for a website that delivers immersive experiences by producing world-class
          virtual reality projects.
        </p>
      </div>
      <div bind:this={AnimatedCard3}>
        <img src={Insure} alt="" />
        <a
          class="block font-[400] text-white text-xl md:text-2xl py-2"
          href="https://davethadev.github.io/insure-landing-page/"
          >Insure landing page</a
        >
        <p class="font-[400] text-[#999999] px-0 pb-14 text-base md:text-lg">
          Another design from <a
            class="text-base md:text-lg text-white"
            href="https://www.frontendmentor.io/challenges/insure-landing-page-uTU68JV8"
            >frontendmentor</a
          > for a website that helps you get life insurance coverage easier and faster.
          They blend expertise and technology to help you find the plan that's just
          right for you.
        </p>
      </div>
      <div bind:this={AnimatedCard4}>
        <img src={Chirp} alt="" />
        <a
          class="block font-[400] text-white text-xl md:text-2xl py-2"
          href="https://davethadev.github.io/Chirp-landing-page/"
          >Chirp landing page</a
        >
        <p class="font-[400] text-[#999999] px-0 pb-14 text-base md:text-lg">
          A design from <a
            class="text-base md:text-lg text-white"
            href="https://www.codewell.cc/challenges/chirp-landing-page--60fc1e36a383e41090a3c71c"
            >codewell</a
          > for a twitter analytics website that helps you better understand your
          audience, which tweets they like and when they are most active.
        </p>
      </div>
    </div>
  </div>
  <div id="about" class="bg-[#6d7f97] py-8 px-4 md:px-0">
    <div
      class="w-full md:w-[85%] h-auto my-0 mx-auto grid grid-cols-1 md:grid-cols-2 gap-0 md:gap-8"
    >
      <div>
        <h2 class="font-[400] text-white text-lg md:text-3xl w-full md:w-96">
          A young man passionate about growth and self development
        </h2>
        <p
          class="font-[400] text-[#d9d9d9] text-base md:text-lg w-full md:w-96 pt-4"
        >
          The experience I've had so far working with frontend web technolgies
          to create appealing user interfaces has allowed me to develop a
          skillset that helps me in not just development, but in every aspect of
          my everyday life.
        </p>

        <p
          class="font-[400] text-[#d9d9d9] text-base md:text-lg w-full md:w-96 pt-4"
        >
          I'm proud to announce that I am continually learning and improving my
          skills so as to open myself to a world of opportunities.
        </p>
      </div>
      <div>
        <p
          class="font-[400] text-[#d9d9d9] text-base md:text-lg w-full md:w-96 pt-4"
        >
          As a developer, I believe I have everything available to me and all
          that is holding me back is myself.
        </p>

        <p
          class="font-[400] text-[#d9d9d9] text-base md:text-lg w-full md:w-96 pt-4"
        >
          A quote I live by perfectly illustrates what I mean.
        </p>

        <p
          class="font-[400] text-[#d9d9d9] text-base md:text-lg w-full md:w-96 pt-4"
        >
          "How big would you dream, if you knew you wouldn't fail?" Even as I
          continue to improve my skills as a developer, I also try to make out
          time for all the other things I'm passionate about.
        </p>

        <p
          class="font-[400] text-[#d9d9d9] text-base md:text-lg w-full md:w-96 pt-4"
        >
          I'm happy to chat over coffe sometime about I can help your company or
          growing business.
        </p>
      </div>
    </div>
  </div>
  <div id="contact-me" class="py-8 px-4 md:px-0 w-full">
    <div class="w-full md:w-[85%] mx-auto my-0">
      <h2 class="font-bold text-white text-lg md:text-3xl">
        Interested in working with me?
      </h2>
      <p
        class="font-[400] text-[#999999] text-base md:text-lg w-auto md:w-96 pt-3"
      >
        I'm active on all social media platforms listed below, but you can also
        send me an email and I will get back to you within 24-48 hours.
      </p>
      <a
        class="block mt-4 mx-0 mb-14 px-2 py-2 rounded w-36 text-center text-base md:text-lg font-[400] text-black bg-yellow-300"
        href="mailto: david_umanah@yahoo.com">Get in touch</a
      >
    </div>
  </div>

  <footer class="bg-[#6d7f97]">
    <div
      class="w-full md:w-[85%] my-0 mx-auto flex items-center justify-between py-4 px-4 md:px-0"
    >
      <div class="font-[400] text-white text-base md:text-lg">David Umanah</div>
      <div class="flex items-center gap-4">
        <a class="block text-xl" href="https://github.com/Davethadev"
          ><Icon icon="mdi:github" style="font-size: 28px" /></a
        >
        <a
          class="block text-xl"
          href="https://www.linkedin.com/in/david-umanah-364a2924b?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app"
          ><Icon icon="mingcute:linkedin-fill" style="font-size: 28px" /></a
        >
        <a class="block text-xl" href="https://mobile.twitter.com/_callmedaveed"
          ><Icon icon="formkit:twitter" style="font-size: 28px" /></a
        >
      </div>
    </div>
  </footer>
</main>

<style lang="postcss">
  :global(html) {
    background-color: hsl(218, 28%, 13%);
  }

  #logo {
    clip-path: polygon(0 100%, 100% 100%, 100% 100%, 0% 100%);
    opacity: 0;
    transform: translateY(20px);
  }

  #header-text {
    clip-path: polygon(0 100%, 100% 100%, 100% 100%, 0% 100%);
    opacity: 0;
    transform: translateY(20px);
  }

  #header-subtext {
    clip-path: polygon(0 100%, 100% 100%, 100% 100%, 0% 100%);
    opacity: 0;
    transform: translateY(20px);
  }
</style>
