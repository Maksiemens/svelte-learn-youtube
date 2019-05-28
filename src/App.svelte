<script>
  let name = 'Svelte';
  $: upperName = name.toUpperCase();
  $: lowerName = name.toLowerCase();

  let counter = 0;
	$: counterClass = counter % 2 === 0 ? 'red' : 'blue';
	$: {
		console.log('Name', name);
		console.log('Counter', counter);
	}
	$: if ( counter === 10 ) {
		name = 'Counter is equal 10';
	}

  const number = 26;
  const src =
    'https://res.cloudinary.com/practicaldev/image/fetch/s--Y5H4oomk--/c_imagga_scale,f_auto,fl_progressive,h_500,q_auto,w_1000/https://thepracticaldev.s3.amazonaws.com/i/c3s8y2nj2safv7q58qs9.png';
  const altText = 'Svelte image';
  const htmlString =
    '<strong>This is strong text</strong> with <em>italic text</em>';

  function changeNameHandler() {
    name = 'New name';
  }

  function mouseMoveHandler(event) {
    pos.x = event.x;
    pos.y = event.y;
  }

  const pos = { x: 0, y: 0 };

  let inputValue = '';

  function submitHandler(event) {
    console.log(inputValue);
  }
</script>

<style>
  h1 {
    color: purple;
  }

  .parent {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 250px;
    height: 125px;
  }

  .parent__img {
    display: block;
    width: 100%;
    height: auto;
    object-fit: cover;
  }

  .playground {
    width: 400px;
    height: 200px;
    padding: 15px;
    margin-top: 30px;
    border: 1px solid blue;
  }

  .blue {
    color: blue;
  }
  .red {
    color: red;
  }
</style>

<h1>{name}</h1>
<h2>{upperName}</h2>
<h2>{lowerName}</h2>
<button on:click={changeNameHandler}>Change name</button>

<h2 class={counterClass}>Counter {counter}</h2>
<button on:click={() => counter++}>Add 1 to counter</button>

<div class="playground" on:mousemove={mouseMoveHandler}>
  <h2>X: {pos.x}, Y: {pos.y}</h2>
</div>

<form on:submit|preventDefault|once={submitHandler}>
  <input type="text" on:input={event => (inputValue = event.target.value)} />
  <button type="submit">Submit form</button>
</form>

<h2>Hello {name}!</h2>
<h2>Hello {name.toUpperCase()}!</h2>
<h2>Hello {(Math.random() * number).toFixed(1)}!</h2>

<div class="parent">
  <img class="parent__img" {src} alt={altText} />
</div>

<p>
  {@html htmlString}
</p>
