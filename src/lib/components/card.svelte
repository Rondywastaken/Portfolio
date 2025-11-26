<script lang="ts">
  import ku from "$lib/assets/ku.svg";
  import next from "$lib/assets/next.jpg";
  import nextproof from "$lib/assets/nextproof.pdf";
  import kuproof from "$lib/assets/kuproof.pdf";
  import el from "$lib/assets/el.png";

  export let type = "";

  let list_edu = [
    { 
      institution: "University of Copenhagen",
      type: "Computer science",
      year_start: "2024",
      year_end: "present",
      img: ku,
      proof: kuproof
    },
    { 
      institution: "Next Education Copenhagen",
      type: "HTX",
      year_start: "2020",
      year_end: "2023",
      img: next,
      proof: nextproof
    }
  ]

  let list_exp = [
    {
      company: "Elgiganten A/S",
      job: "Service- and Warehouse Assistent",
      year_start: "2022",
      year_end: "2024",
      img: el,
    }
  ]
</script>

{#if type == "Education"}
  {#each list_edu as card}
    <div class="card">
      <img src={card.img} alt={card.img}>
      <p>
        <small>{card.year_start} - {card.year_end}</small> <br>
        <strong>{card.institution}</strong> <br>
        {card.type}
      </p>
      <a href={card.proof} target="_blank">Certificate</a>
    </div>
  {/each}
{:else}
  {#each list_exp as card}
    <div class="card">
      <img src={card.img} alt={card.img}>
      <p>
        <small>{card.year_start} - {card.year_end}</small> <br>
        <strong>{card.company}</strong> <br>
        {card.job}
      </p>
    </div>
  {/each}
{/if}

