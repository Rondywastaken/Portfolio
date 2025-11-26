<script lang="ts">
  import Navbar from "$lib/components/navbar.svelte";
  import Project from "$lib/components/project.svelte";
  import Footer from "$lib/components/footer.svelte";
</script>

<div id="app">
  <header>
    <div id="content-header">
      <Navbar />
    </div>
  </header>
  <div id="content-container">
  <div id="title_">
    <h1>Projects</h1>
  </div>
    <div id="content-body-projects">
      <Project />
    </div>
    <Footer />
  </div>
</div>
