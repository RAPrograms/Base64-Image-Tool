<script lang="ts">
    import { state } from "../lib/state.svelte"

    async function handle_file({target}:{target: HTMLInputElement}){
        const files = target.files
        if(files == undefined || files.length <= 0)
            return

        const [data, error] = await new Promise<[string, any]>((resolve, reject) => {
            const reader = new FileReader();
            reader.readAsDataURL(files[0]);
            reader.onload = () => resolve([reader.result as string, null])
            //@ts-ignore
            reader.onerror = (err) => resolve([null, err])
        })
        if(error)
            return

        state.value = data.substring(data.indexOf(',') + 1)
    }
</script>

<section>
    <label>
        <input type="file" oninput={handle_file}>
        <div>
            <div>Click here</div>
            <div>or</div>
            <div>Drop image file here</div>
        </div>
    </label>
</section>

<style lang="scss">
    section{
        display: contents;
    
        & > label {
            background-color: #3E3E42;
            place-content: center;
            grid-area: Image;
            display: grid;
            padding: 10px;
            flex-grow: 1;

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
                padding: 50px;
                display: flex;
                width: 100%;
            }
        }
    }
</style>