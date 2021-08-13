<script>
    import Modal from './Modal.svelte';
    export let tuote = '';
    export let kplMaara='';
    export let tuoteOsasto='';
    import Button from './Button.svelte';
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    const lisaa = () => dispatch('lisaa', { tuote: tuote, kplMaara: kplMaara, tuoteOsasto: tuoteOsasto});
    const nollaa = () => dispatch('nollaa');

    function onkoMerkkeja(x) {
        return x.trim().lenght === 0;
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
    <label>Tuote<input bind:value={tuote} /></label>
    <label>KPL Määrä<input bind:value={kplMaara} /></label>
    <label>Tuote-Osasto<input bind:value={tuoteOsasto} /></label>
    <div slot="footer">
        {#if !validitArvot}
            <p>Kaikki kentät ovat pakollisia!</p>
        {/if}
        <Button on:click={lisaa} disabled={!validitArvot}>Lisää</Button>
        <Button on:click={nollaa}>peruuta</Button>
    </div>
</Modal>