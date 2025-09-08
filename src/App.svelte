<script lang="ts">
  import "./main.scss"

  import ImagePane from "./components/ImagePane.svelte";
  import FieldPane from "./components/FieldPane.svelte";
  import Footer from "./components/Footer.svelte";
  import Header from "./components/Header.svelte";

  let textState = $state({ text: "hello" });
  $effect(() => {
    console.log(textState)
  })
</script>

<main>
  <Header/>

  <ImagePane/>

  <FieldPane bind:state={textState}/>

  <Footer/>
</main>