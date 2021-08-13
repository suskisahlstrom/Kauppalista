<script>
    export let tuote;
    export let kplMaara;
    export let tuoteOsasto;
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    const poista = () => dispatch('poista', {tuote: tuote, kplMaara: kplMaara, tuoteOsasto: tuoteOsasto});
  </script>
  
  <article>
    <div class="card">
      <p>{tuote}</p>
      <p>{kplMaara}</p>
      <p>{tuoteOsasto}</p>
      <div class="nappi">
        <button on:click={poista}>Poista</button>
      </div>
    </div>
  </article>