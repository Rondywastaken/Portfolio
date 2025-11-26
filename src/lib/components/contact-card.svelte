<script lang="ts">
  let cards = [
    {
      contact_method: "Email",
      description: "ronitem19@gmail.com",
      description_clickable: true,
      button_text: "Send Message",
      button_method: "mailto",
      link: "",
      copied: false,
    },
    {
      contact_method: "LinkedIn",
      description: "Connect with me",
      description_clickable: false,
      button_text: "Visit Profile",
      button_method: "",
      link: "https://www.linkedin.com/in/roni-temizsoy-663b2b384",
      copied: false,
    },
    {
      contact_method: "GitHub",
      description: "Check out my projects",
      description_clickable: false,
      button_text: "View Repositories",
      button_method: "",
      link: "https://github.com/Rondywastaken",
      copied: false,
    },
    {
      contact_method: "Phone",
      description: "+45 31 16 55 93",
      description_clickable: true,
      button_text: "Call Me",
      button_method: "tel",
      link: "",
      copied: false,
    }
  ];
  
  const copyClipboard = async (card_index: any) => {
    let copy_parsed = cards[card_index].description.replaceAll(" ", "");
    navigator.clipboard.writeText(copy_parsed);
    cards[card_index].copied = true;
    setTimeout(() => {
      cards[card_index].copied = false;
    }, 2000);
  }
</script>

{#each cards as card, i}
  <div class="contact-card">
    <h3>{i+1}.</h3>
    <h4><strong>{card.contact_method}</strong></h4>
    {#if card.description_clickable}
      {#if !card.copied}
        <button onclick={() => copyClipboard(i)}>
          {card.description}<i class="fa-solid fa-copy"></i>
        </button>
      {:else}
        <p>Copied!</p>
      {/if}
      <a href={card.button_method + ":" + card.description}>
        {card.button_text}
      </a>
    {:else}
      <p>{card.description}</p>
      <a href={card.link} target="_blank">{card.button_text}</a>
    {/if}
  </div>
{/each}
