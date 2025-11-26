<script lang="ts">
  import Navbar from "$lib/components/navbar.svelte";
  import Footer from "$lib/components/footer.svelte";
  import ContactCard from "$lib/components/contact-card.svelte";
</script>

<div id="app">
  <header>
    <div id="content-header">
      <Navbar />
    </div>
  </header>
  <div id="title_">
    <h1>Contact Me</h1>
    <p>Reach out to me through any of these channels.</p>
  </div>
  <div id="content-container">
    <div id="contact-cards">
      <ContactCard />
    </div>
    <Footer />
  </div>
</div>
