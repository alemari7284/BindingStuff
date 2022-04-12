<script>
  export let val;

  export function empty() {
    val = "";
  }
</script>

<input style="background-color: red;" type="text" bind:value={val} />
