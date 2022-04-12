<script>
  export let chosenOption = 1;
</script>

<button disabled={chosenOption === 1} on:click={() => (chosenOption = 1)}
  >Opt 1</button
>
<button disabled={chosenOption === 2} on:click={() => (chosenOption = 2)}
  >Opt 2</button
>
