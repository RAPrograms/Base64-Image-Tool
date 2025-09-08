<section>
    <header>Base 64 String</header>
    <textarea placeholder="Paste the base 64 image string here"></textarea>
    <button>Clear All</button>
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
            --background-colour: #1C1A27;

            background: var(--background-colour);
            border-radius: 10px;
            text-align: center;
            padding: 10px 3px;
            margin: 10px auto;
            cursor: pointer;
            border: none;
            width: 90%;

            &:hover{
                background: color-mix(in hsl shorter, var(--background-colour), white 20%);
            }
        }
    }
</style>