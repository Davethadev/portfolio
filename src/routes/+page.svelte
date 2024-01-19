<script>
  import Navbar from "../components/Navbar.svelte";
  import Hero from "../components/Hero.svelte";
  import Works from "../components/Works.svelte";
  import About from "../components/About.svelte";
  import Contact from "../components/Contact.svelte";
  import Footer from "../components/Footer.svelte";
</script>

<main class="w-full">
  <header class="h-auto md:h-[100vh]">
    <Navbar />
    <Hero />
  </header>
  <section>
    <Works />
    <About />
    <Contact />
    <Footer />
  </section>
</main>

<style lang="postcss">
  
  :global(html) {
    background-color: hsl(218, 28%, 13%);
  }
</style>
