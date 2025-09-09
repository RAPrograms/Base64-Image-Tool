<script lang="ts">
  import "./main.scss"

  import ImagePane from "./components/ImagePane.svelte";
  import FieldPane from "./components/FieldPane.svelte";
  import Footer from "./components/Footer.svelte";
  import Header from "./components/Header.svelte";

  let img_component: ImagePane
  let field_component: FieldPane

  async function render_string(value: string){
    
  }
</script>

<main>
  <Header/>

  <ImagePane bind:this={img_component} onchange={(value: string) => field_component.change_value(value)}/>

  <FieldPane bind:this={field_component} onchange={(value: string) => img_component.set_string(value)}/>

  <Footer/>
</main>