<script>
  import html2canvas from 'https://unpkg.com/html2canvas@1.4.1/dist/html2canvas.esm.js?module';
  import { onMount } from 'svelte';
  let cnvURL;
  
  function genImg(e){
    console.log('genImg', e)
    html2canvas(document.getElementsByClassName("src-table")[0]).then((canvas)=>{
document.querySelector('.genImgOut').innerHTML="";      document.querySelector('.genImgOut').appendChild(canvas)
    });
  }
  // generate a download link from the canvas obj

 function genLink(){
   let cn = document.querySelector('.genImgOut canvas');
   cnvURL = cn.toDataURL("img/png");
   document.querySelector('.dlImg').innerHTML = '';
   document.querySelector('.dlImg').innerHTML = `<a download='myPixelArt.png' href="${cnvURL}">download</a>`
 } 
onMount(()=>{
  // listen for dom changes to genImgOut before generating a download link
  console.log('Save svelte mounted')
  let targetDom = document.querySelector('.genImgOut');
let config = { childList: true };
const callBack = ( mutationList, observer) => {
  for( const mutation of mutationList){
    if(mutation.type == 'childList'){
      console.log('changed the dom! ');
      genLink();
    }
  }
}
const observer = new MutationObserver(callBack);
observer.observe(targetDom, config); 
})

  /**
 
  **/
</script>
<hr/>
<button on:click={genImg}>Generate Image</button>
<div class="genImgOut"></div>
<div class="dlImg"></div>
