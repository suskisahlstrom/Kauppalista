<script>
	export let name;
	import Modal from './Modal.svelte';
	import Button from './Button.svelte';
	import Checkout from './Checkout.svelte';

	

	let checkoutVisible = false;

	function LisaaTuote(){
		checkoutVisible = true;
	}
	
</script>

<main>
	<h1>{name}</h1>
	<label for="Lisää" />
	<Button
		type="Button"
		id="Lisää"
		on:click={LisaaTuote}>Lisää
	</Button>
    

</main>
{#if checkoutVisible}
  <Checkout on:peruutettu={peruutaTilaus} on:maksettu={tilausMaksettu} />
{/if}
<style>
	
	main {
		padding: 1em;
		margin: 0 auto;
	}

	h1 {
		color: #fa4fe3;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
	
	
		
	
</style>