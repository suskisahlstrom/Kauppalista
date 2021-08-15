<script>
    import Modal from './Modal.svelte';
    export let tuote = '';
    export let kplMaara='';
    export let tuoteOsasto='';
    import Button from './Button.svelte';
    import { createEventDispatcher } from 'svelte';  
    const dispatch = createEventDispatcher(); // eventin importtaus ja luonti
    const lisaa = () => 
        dispatch('lisaa', { tuote: tuote, kplMaara: kplMaara, tuoteOsasto: tuoteOsasto});
    const nollaa = () => dispatch('nollaa');

    function onkoMerkkeja(teksti) {    //Tuotteiden lisäyslaatikoiden validointi. Jostain syystä validointi ei toimi mutta pienellä muutoksella se toimii liiankin hyvin eikä anna lisätä mitään.
        return teksti.trim().lenght === 0;
    }
    $: tuoteValid = !onkoMerkkeja(tuote);
    $: kplMaaraValid = !onkoMerkkeja(kplMaara);
    $: tuoteOsastoValid = !onkoMerkkeja(tuoteOsasto);
    $: validitArvot = tuoteValid && kplMaaraValid && tuoteOsastoValid;
</script>

<Modal>
    <div slot="header">
        <h1>Uusi Tuote</h1>
    </div>
    <label>Tuote<input bind:value={tuote} /></label>  <!--Tuotteiden lisäyskentät-->
    <label>KPL Määrä<input bind:value={kplMaara} /></label>
    <label>Tuote-Osasto<input bind:value={tuoteOsasto} /></label> 
    <div slot="footer">
        {#if !validitArvot}
            <p>Kaikki kentät ovat pakollisia!</p> 
        {/if}
        <Button on:click={lisaa} disabled={!validitArvot}>Lisää</Button> <!--Lisää ja peruuta napit-->
        <Button on:click={nollaa}>Peruuta</Button>
    </div>
</Modal>