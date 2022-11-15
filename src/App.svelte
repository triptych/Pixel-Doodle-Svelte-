<script>
  //import logo from './assets/svelte.png'
  //import Counter from './lib/Counter.svelte'
  import Grid from './lib/Grid.svelte';
  import Colorpicker from './lib/Colorpicker.svelte';
  import Save from './lib/Save.svelte';
</script>
<header>
  <h1> Pixel Doodle v 1.0.1</h1>
  <p>
    Click a pixel to color it in. 
    Choose color via picker below.
    Click 'Generate Image' to create a png.
    Click 'download' link to save.
    (TIP: turn off border right before saving.)
  </p>
</header>
<main>
  <Grid rows="10" cols="10"/>
  <Colorpicker /> 
  <Save />
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    background-color: tan;
  }

  </style>

