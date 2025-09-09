<script lang="ts">
    let string = $state("")
    let file_over = $state(false)

    let { onchange } : { onchange: (value: string) => void } = $props()

    export function set_string(value: string){
        string = value
    }

    function to_base_64(data){
        return new Promise<[string, any]>((resolve) => {
            const reader = new FileReader();
            reader.readAsDataURL(data);
            reader.onload = () => resolve([reader.result as string, null])
            //@ts-ignore
            reader.onerror = (err) => resolve([null, err])
        })
    }

    async function handle_file({target}:{target: HTMLInputElement}){
        file_over = false

        const files = target.files
        if(files == undefined || files.length <= 0)
            return

        const [data, error] = await to_base_64(files[0])
        if(error)
            return

        string = data.substring(data.indexOf(',') + 1)
        onchange(string)
    }

    async function handle_drop(e){
        e.preventDefault()
        file_over = false
        if(e.dataTransfer.items.length <= 0)
            return

        const [data, error] = await to_base_64(e.dataTransfer.items[0].getAsFile())
        if(error)
            return

        string = data.substring(data.indexOf(',') + 1)
        onchange(string)
    }
</script>

<svelte:window ondrop={handle_drop} ondragover={(e) => {
    e.preventDefault()
    file_over = true
}} ondragleave={() => {file_over = false}}/>

<section>
    {#if string != ""}
        <img src="data:image/jpg;base64,{string}" alt="" onerror={() => {
            string = ""
            alert("Invalid Image")
        }}>
    {/if}
    <label class:file_hover={file_over} >
        <input type="file" oninput={handle_file}>
        <div class:hover={file_over && string != ""}>
            <div>Click here</div>
            <div>or</div>
            <div>Drop image file here</div>
        </div>
    </label>
</section>

<style lang="scss">
    section{
        background-color: #3E3E42;
        place-content: center;
        position: relative;
        grid-area: Image;
        display: grid;
        padding: 10px;
        flex-grow: 1;
        
        & > img{
            translate: -50% -50%;
            position: absolute;
            max-height: 100%;
            max-width: 100%;
            z-index: 0;
            left: 50%;
            top: 50%;
        }

        & > img ~ label.file_hover::after{
            content: "";
            width: 100%;
            position: absolute;
            height: 100%;
            z-index: 1;
            background-color: rgba(0, 0, 0, 0.4);

            & > div{
                visibility: visible;
                display: block;
            }
        }

        & > img ~ label:not(.file_hover) > div{
            visibility: none;
            display: none;
        }
        
    
        & > label {
            display: contents;
            z-index: -1;

            & > input[type=file]{
                display: none;
            }

            & > div{
                border: 2px dashed white;
                justify-content: center;
                flex-direction: column;
                align-items: center;
                text-align: center;
                border-radius: 2%;
                aspect-ratio: 1/1;
                max-width: 500px;
                cursor: pointer;
                padding: 50px;
                display: flex;
                width: 100%;
                z-index: 2;
            }
        }
    }
</style>