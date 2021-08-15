<script>
    export let tuote;
    export let kplMaara;
    export let tuoteOsasto;
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    const poista = () => dispatch('poista', tuote);
  </script>
  
  <article> <!--Lisättyjen tuotteiden "kortti" joka ilmestyy tuotteen lisäämisen jälkeen, jostain syystä koodi luo valmiiksi yhden tyhjän kortin jota ei voi poistaa.-->
    <div class="card">
      <p>{tuote}</p>
      <p>{kplMaara} KPL</p>
      <p>{tuoteOsasto}</p>
      <div class="button">
        <button on:click={poista}>Poista</button> <!--Tuotten poistonappi-->
      </div>
    </div>
  </article>

<style>
  .card {
    border: black;
    border-radius: 5px;
    background-color: white;
    max-width: 240px;
    margin-left: 120px;
    font-size: 18px;
     }
  
  
</style>