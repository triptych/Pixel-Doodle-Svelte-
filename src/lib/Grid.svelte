<script>
  import {color} from './stores.js';
  export let rows = 0;
  export let cols = 0;
  let clickColor;
  let border=true;

  color.subscribe( value=> {
    clickColor = value;
  })
  function clickCell(e){
    console.log('clickCell e', e);
    console.log('clickColor:', clickColor);
    e.target.style.backgroundColor=`${clickColor}`
  }
</script>

<table class:noborder={!border} class="src-table">
  {#each Array(parseInt(rows)) as _, index (index)}
    <tr>
      {#each Array(parseInt(cols)) as _, index (index)}
      <td on:click={clickCell}></td>
      {/each}
    </tr>
  {/each}
</table>
<label for="borderel">border</label><input id="borderel" type="checkbox"  class="input-border" bind:checked={border}/>

<style>
  table {
    border: 0;
    border-spacing: 0;
    background-color: #fff;
  }
  tr {
    border:0;
  }
  td {
    border: 1px solid black;
    height: 20px;
    width: 20px;
    padding: 0;
    margin: 0;
    cursor: pointer;
  }

  .noborder td{
    border: 0;
  }

  
</style>