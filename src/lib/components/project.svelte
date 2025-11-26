<script lang="ts">
  let projects = [
    {
      name: "Audio Engine",
      description: "Audio implementation for a 2D game engine called DIKUArcade, introducing playback audio.",
      tags: ["C#", "Game Engine", "Raylib-cs"],
      link: "https://github.com/Rondywastaken/DIKUArcadeAudioEngine/tree/AudioEngine"
    },
    {
      name: "FitFriend",
      description: "Fitness app to create competitions with your friends, for a final school project.",
      tags: ["Typescript", "Sveltekit", "Pocketbase"],
      link: "https://github.com/Rondywastaken/DDU_Projekt"
    },
    {
      name: "PassProtector",
      description: "Password manager to create and manage passwords, for a final school project",
      tags: ["Typescript", "Sveltekit", "Pocketbase"],
      link: "https://github.com/AndreasZacchi/passprotector"
    },
  ];
  export let amount = projects.length;
</script>

{#each projects.slice(0, amount) as p}
  <div class="project">
    <h5>{p.name}</h5>
    <small><p>{p.description}</p></small>
    <div>
      {#each p.tags as t}
        <span class="tags">{t}</span> 
      {/each}
    </div>
    <a href={p.link} target="_blank"><i class="fa-brands fa-github"></i>Repository</a>
  </div>
{/each}
