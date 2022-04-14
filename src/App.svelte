<script>
  //end section 8
  import CustomInput from "./CustomInput.svelte";
  import Toggle from "./Toggle.svelte";
  import { isValidEmail } from "./validation";

  let val = "Alex";
  let price = 0;
  let selectedOpt = 1;
  let agreed = false;
  let favColor = ["red"];
  let singleFavColor = "red";
  let usernameInput;
  let someDiv;
  let customInput;
  let enteredEmail = "";
  let formIsValid = false;

  $: formIsValid = enteredEmail.includes("@") ? true : false;

  $: console.log(agreed);
  $: console.log(val);
  $: console.log(selectedOpt);
  $: console.log(price);
  $: console.log(favColor);
  $: console.log(singleFavColor);

  const setValue = (event) => {
    val = event.target.value;
  };

  const saveData = () => {
    console.log(usernameInput.value);
    console.log(usernameInput);
    console.dir(someDiv);
    console.log(customInput);
    customInput.empty();
  };
</script>

<input style="background-color: green;" type="text" value={val} />

<input style="background-color: yellow;" type="text" bind:value={val} />

<CustomInput bind:val bind:this={customInput} />
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

<hr />

<input type="text" id="username" bind:this={usernameInput} />
<button on:click={saveData}>Save</button>

<div bind:this={someDiv}>just a div</div>

<hr />

<form on:submit|preventDefault>
  <input
    type="email"
    bind:value={enteredEmail}
    class={isValidEmail(enteredEmail) ? "" : "invalid"}
  />
  <button type="submit" disabled={!formIsValid}>Save</button>
</form>

<style>
  .invalid {
    border: 3px solid red;
  }
</style>
