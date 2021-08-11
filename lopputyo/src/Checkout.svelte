<script>
    import Button from './Button.svelte';
    import Lisays from './Lisays.js';
    import Modal from './Modal.svelte';


    import { createEventDispatcher } from 'svelte';
import TextInput from './TextInput.svelte';
    const dispatch = createEventDispatcher();
    let tuoteOsasto = [
		{ nimi: 'Hevi'},
		{ nimi: 'Leipä'},
		{ nimi: 'Eines'},
		{ nimi: 'Liha'},
		{ nimi: 'Juusto'},
		{ nimi: 'Maito'},
		{ nimi: 'Kuiva-aineet'},
		{ nimi: 'Juomat'},
		{ nimi: 'Herkut'},
	];
    let maara = [
		{ nimi: '1'},
		{ nimi: '2'},
		{ nimi: '3'},
		{ nimi: '4'},
		{ nimi: '5'},
		{ nimi: '6'},
		{ nimi: '7'},
		{ nimi: '8'},
		{ nimi: '9'},
	];

    let tuote, kplmaara, tuoteosasto;
	function LisaaTuote() {
		const lisattavat = {
			tuote: tuote,
			kplmaara: kplmaara,
			tuoteosasto: tuoteosasto,
		};
		Lisays.set(lisattavat)
		
	}
    
    function peruutaLisays() {
        dispatch('Peruutettu');
    }

    function lisaaTuotteet() {
        dispatch('Lisätty')
    }
</script>

<Modal on:click>
    <h1 slot="header">Lisää tuote</h1>

    <div class="box">
        <span class="liftup">Tuotetiedot</span>
        <TextInput
            type="text"
            label="Tuote"
            value={tuote}
            id="tuote"
            on:input={(e) => (tuote = e.EventTarget.value)}
            valid={validiTuote}
            error={'Kenttä ei voi olla tyhjä'}
        />
        <label for="määrä">Kpl määrä</label>
        <select bind:value={kplmaara} id="määrä">
        {#each maara as koko}
          <option value={koko}>{koko.nimi}</option>
        {/each}
      </select>

    </div>

    <div slot="footer">
        <Button id="Peruuta" on:click={peruutaLisays}>Peruuta</Button>
        <Button id="Lisää" on:click={lisaaTuotteet}>Lisää</Button>
    </div>
</Modal>

<style>
    .box {
        padding: 1em;
        border: 1px solid #cccccc;
        box-shadow: 0px 5px 10px #cccccc;
        margin-bottom: 1em;
    }
    .red {
    background-color: #000000;
    color: #ee9edd;
    padding: 1em;
    margin-top: 1em;
    margin-bottom: 1em;
  }
  progress {
    width: 100%;
  }
</style>