<script>
	const tuotte = {haku: 'tuote', laji: 'tuote'};
	let naytakentat = false;
  
	let tuote = ''; // Määritellään tuotteiden kategoriat
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
	  tuotteet.push({ tuote: tuote, kplMaara: kplMaara, tuoteOsasto: tuoteOsasto }); 
	  tuotteet = tuotteet;
	};
	let lisatytTuotteet = [
		
	];

	const poistaTuote = (ce) => { // Funktio tuotteiden poistamista varten
	  lisatytTuotteet = lisatytTuotteet.filter((tuot) => tuot.tuote !== ce.detail);
	};
	const lisaaTuote = (ce) => {  // Funktio tuotteiden lisäämiseen
	  lisatytTuotteet.push(ce.detail);
	  lisatytTuotteet = lisatytTuotteet;
	  naytakentat = false;
	};
  </script>
  
  <main>
	<Otsikko />
	<Tiedot {tuote} {kplMaara} {tuoteOsasto}  /> <!--Haetaan tiedot.sveltestä tietokortit pääsivulle-->
	{#if naytakentat}
	  <UusiTuote on:lisaa={lisaaTuote} on:nollaa={() => (naytakentat = false)} /> <!--if funktio joka lukee onko popup ikkunassa painettu lisää nappia tai peruuta nappia ja sulkee ikkunan-->
	{/if}
	<Button on:click={() => (naytakentat = !naytakentat)}>Lisää</Button>
	<Tuotteet {lisatytTuotteet} {tuotte} on:poista={poistaTuote} />
  </main>
  
  <style>
	main {
	  text-align: center;
	  padding: 1em;
	  max-width: 480px;
	  margin: 0 auto;
	  font-size: 20px;
	}
  </style>
  