<script lang="ts">
  import Navbar from "$lib/components/navbar.svelte";
  import image from "$lib/assets/image.webp";
  import resume from "$lib/assets/resume.pdf";
  import { onMount } from "svelte";
  import Card from "$lib/components/card.svelte";
  import { goto } from "$app/navigation";
  import Project from "$lib/components/project.svelte";
  import Footer from "$lib/components/footer.svelte";
  
  let selectorActive = $state("Education");

  const changeSelector = (selector: string) => {
    selectorActive = selector;
    localStorage.setItem("selector-active", selectorActive);
  }

  onMount(() => {
    selectorActive = localStorage.getItem("selector-active")!;
  });
</script>

<div id="app">
  <header>
    <div id="content-header">
      <Navbar />
    </div>
  </header>
  <div id="content-container">
    <div id="content-body">
      <div id="about-section">
        <div id="text">
          <h2>Roni Temizsoy</h2>
          <p>
            Computer Science BSc student, <strong>University of Copenhagen</strong>
          </p>
          <div id="about-links">
            <a id="resume" href={resume} target="_blank">
              Resume<i class="fa-solid fa-download"></i>
            </a>
            <!-- svelte-ignore a11y_consider_explicit_label -->
            <a class="link" target="_blank" href="https://www.linkedin.com/in/roni-temizsoy-663b2b384">
              <i class="fa-brands fa-linkedin"></i>
            </a>
            <!-- svelte-ignore a11y_consider_explicit_label -->
            <a class="link" target="_blank" href="https://github.com/Rondywastaken">
              <i class="fa-brands fa-github"></i>
            </a>
            <!-- svelte-ignore a11y_consider_explicit_label -->
            <a class="link" target="_blank" href="mailto:ronitem19@gmail.com">
              <i class="fa-regular fa-envelope"></i>
            </a>
          </div>
        </div>
        <img id="pfp" src={image} alt="pfp">
      </div>
      <div id="work-education-section">
        <div id="selector">
          <button 
            onclick={() => changeSelector("Education")}
            class:active={selectorActive == "Education"}>
            Education
          </button>
          <button 
            onclick={() => changeSelector("Experience")}
            class:active={selectorActive == "Experience"}>
            Experience
          </button>
        </div>
        <div id="education-work-container">
          {#if selectorActive == "Education"}
            <Card type="Education" />
          {:else}
            <Card type="Experience" />
          {/if}
          <span id="line"></span>
        </div>
      </div>
      <div id="projects-overview">
        <div id="projects-overview-title">
          <h2>Projects Overview</h2>   
          <small><p onclick={() => goto("/projects")}>
            See all <i class="fa-solid fa-arrow-right"></i>
          </p></small>
        </div>
        <div id="projects">
          <Project amount={2} />
        </div>
      </div>
    </div>
    <Footer />
  </div>
</div>
