<script>
	export let name;
	import Modal from './modal.svelte';
	import button from './button.svelte';
	let LisääTuoteSivu = false;
	function LisääTuote() {
		LisääTuoteSivu = true;
	}
</script>

<main>
	<h1>{name}</h1>
	<label for="Lisää" />
	<Button
		type="button"
		id="Lisää"
		on:click={LisääTuote}>Lisää
	</Button>
    

</main>

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