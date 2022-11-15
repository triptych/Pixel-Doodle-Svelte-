<script>
  import {color} from './stores.js';
  let inColor = 'black'
  function handleChange (e) {
    console.log('handleChange called. e:', e);
    color.set(e.target.value)
    inColor = e.target.value
  }
</script>

<input type="color" on:input={handleChange} />
<b>color: {inColor}</b>