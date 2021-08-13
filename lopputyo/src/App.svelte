<script>
	const elain = { };
	let h = 0;
	let naytakentat = false;
  
	let tuote = '';
	let kplMaara = '';
	let tuoteOsasto = '';
	const nollaa = () => {
	  tuote = '';
	  kplMaara = '';
	  tuoteOsasto = '';
	};
	import Otsikko from './Otsikko.svelte';
	import Tiedot from './Tiedot.svelte';
	import Button from './Button.svelte';
	import Tuotteet from './Tuotteet.svelte';
	import UusiTuote from './UusiTuote.svelte';
  
	let lisaa = () => {
	  lemmikit.push({ tuote: tuote, kplMaara: kplMaara, tuoteOsasto: tuoteOsasto });
	  lemmikit = lemmikit;
	};
	let elaimet = [
	  
	];
	const poistaKoira = (ce) => {
	  elaimet = elaimet.filter((nim) => nim.nimi !== ce.detail);
	};
	const lisaaElain = (ce) => {
	  elaimet.push(ce.detail);
	  elaimet = elaimet;
	  naytakentat = false;
	};
  </script>
  
  <main>
	<Otsikko />
	<Tiedot {tuote} {kplMaara} {tuoteOsasto}  />
	{#if naytakentat}
	  <UusiTuote on:lisaa={lisaaElain} on:nollaa={() => (naytakentat = false)} />
	{/if}
	<Button on:click={() => (naytakentat = !naytakentat)}>Tiedot</Button>
	<Tuotteet {elaimet} {elain} on:poista={poistaKoira} />
  </main>
  
  <style>
	main {
	  text-align: center;
	  padding: 1em;
	  max-width: 240px;
	  margin: 0 auto;
	}
  
	@media (min-width: 640px) {
	  main {
		max-width: none;
	  }
	}
  </style>
  