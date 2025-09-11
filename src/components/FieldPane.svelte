<script lang="ts">
    const { onchange } : { onchange: (data: string) => void } = $props()

    let textarea: HTMLTextAreaElement
    let delay: number | undefined
    let active = $state(false)

    function handle_change(){
        clearTimeout(delay)
        delay = setTimeout(() => {
            onchange(textarea.value)
            active = textarea.value != ""
        }, 300)
    }

    export function change_value(value: string){
        textarea.value = value
        active = value != ""
    }

    function clear(){
        textarea.value = ""
        onchange("")
        active = false
    }
</script>

<section>
    <header>Base 64 String</header>
    <textarea bind:this={textarea} oninput={handle_change} placeholder="Paste the base 64 image string here"></textarea>
    <button disabled={!active} onclick={clear}>Clear All</button>
</section>

<style lang="scss">
    section{
        background-color: #3E3E42;
        flex-direction: column;
        border-radius: 5px;
        grid-area: Field;
        display: flex;

        & > header{
            border-bottom: 1px solid white;
            padding-bottom: 2px;
            text-align: center;
            font-size: large;
            font-weight: 600;
            margin: 0 10px;
        }

        & > textarea{
            padding: 10px 10px 0 10px;
            background: none;
            border: none;
            flex-grow: 1;

            @media (width < 500px) {
                min-height: 150px;
                resize: vertical;
            }
        }

        & > button{
            --background-colour: #a13838;

            background-color: var(--background-colour);
            transition: 350ms all ease-out;
            border-radius: 10px;
            text-align: center;
            padding: 10px 3px;
            margin: 10px auto;
            cursor: pointer;
            border: none;
            width: 90%;

            &:disabled{
                background-color: rgba(128, 128, 128, 0.341);
                opacity: 0.4;
            }
        

            &:not(:disabled):hover{
                background-color: color-mix(in srgb, transparent 30%, var(--background-colour));
                transition: 150ms all ease-in;
            }
        }
    }
</style>