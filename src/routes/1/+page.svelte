<script lang="ts">
  const prompts = [
    "Enter your name:",
    "Enter your age:",
    "What school do you go to?",
    "What year are you in?",
    "When are you graduating?",
    "What is your major?",
    "Dogs or cats?",
    "How much do you make a year?",
    "Enter your favorite potential cat name:",
    "Give a happy quote for the next person :)",
    "Do you want the $1,000,000?",
    "Do you really want the $1,000,000?",
    "Do you REALLY REALLY want the $1,000,000?"
  ];
  let active = [];
  let ind = 1;

  function add_section() {
    active.push(prompts[ind % prompts.length]);
    active = active;
    ind++;
  }
</script>

<div class="form-holder">
  <div class="top-space"></div>
  <div class="form">
    <h1 class="large-text form-title">Fill out this form for $1,000,000!!!</h1>
    <div class="input-prompt">
      <p class="small-text">{prompts[0]}</p>
      <input type="text" class="xs-text" placeholder="Type here..."/>
    </div>
    {#each Object.entries(active) as [_, prompt]}
      <div class="input-prompt appear">
        <p class="small-text">{prompt}</p>
        <input type="text" class="xs-text" placeholder="Type here..."/>
      </div>
    {/each}
    <div class="submit-button-holder">
      <div
        on:click={add_section}
        on:keydown={(e) => {
          if (e.key === 'Enter') add_section();
        }}
        role="button"
        aria-pressed="false"
        tabindex="0"
      >
        <img class="submit-button" src="/icons/check.svg" alt="Submit"/>
      </div>
    </div>
  </div>
</div>

<style>
  .form-holder {
    width: 70%;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .top-space {
    width: 100%;
    height: 20vh;
    min-height: 3rem;
  }
  .form {
    min-height: 20rem;
    margin-bottom: 3rem;
    width: 55%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
    border-radius: 1.5vw;
    border: 2px solid color-mix(in srgb, var(--bg-color) 65%, var(--font-color) 35%);
    background-color: color-mix(in srgb, var(--bg-color) 95%, white 5%);
  }
  .form-title {
    text-align: center;
  }
  .input-prompt {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    width: 60%;
    margin-top: 2rem;
    margin-bottom: 2rem;
  }
  .input-prompt > p {
    margin-top: 0;
    margin-bottom: 0.5rem;
  }
  .input-prompt > input {
    width: 100%;
    background-color: transparent;
    border: none;
    color: color-mix(in srgb, var(--font-color) 90%, transparent 10%);
    border-bottom: 1px solid color-mix(in srgb, color-mix(in srgb, var(--bg-color) 65%, var(--font-color) 35%) 80%, transparent 20%);
  }
  .submit-button-holder {
    width: 65%;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
  }
  .submit-button-holder > div {
    width: 12.5%;
  }
  .submit-button {
    aspect-ratio: 1/1;
    filter: invert(1);
    --webkit-filter: invert(1);
    width: 100%;
    transition: 0.2s;
  }
  .submit-button:hover {
    transform: scale(1.15);
    filter: invert(0.5);
    --webkit-filter: invert(0.5);
  }
  .appear {
    opacity: 0;
    animation-delay: 0s;
    animation-duration: 1s;
    animation-name: fadein;
    animation-fill-mode: forwards;
  }
  @keyframes fadein {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
</style>
