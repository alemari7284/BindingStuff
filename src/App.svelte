<script>
  import CustomInput from "./CustomInput.svelte";
  import Toggle from "./Toggle.svelte";

  let val = "Alex";
  let price = 0;
  let selectedOpt = 1;
  let agreed = false;
  let favColor = ["red"];
  let singleFavColor = "red";

  $: console.log(agreed);
  $: console.log(val);
  $: console.log(selectedOpt);
  $: console.log(price);
  $: console.log(favColor);
  $: console.log(singleFavColor);

  const setValue = (event) => {
    val = event.target.value;
  };
</script>

<input style="background-color: green;" type="text" value={val} />

<input style="background-color: yellow;" type="text" bind:value={val} />

<CustomInput bind:val />
<Toggle bind:chosenOption={selectedOpt} />
<input type="number" bind:value={price} />

<label>
  <input type="checkbox" bind:checked={agreed} />
</label>

<h1>Favorite color?</h1>
<label>
  <input name="color" type="radio" value="red" bind:group={favColor} />
  Red
</label>
<label>
  <input name="color" type="radio" value="green" bind:group={favColor} />
  Green
</label>
<label>
  <input name="color" type="radio" value="blue" bind:group={favColor} />
  Blue
</label>

<select bind:value={singleFavColor}>
  <option value="green">Green</option>
  <option value="red">Red</option>
  <option value="blue">Blue</option>
</select>
