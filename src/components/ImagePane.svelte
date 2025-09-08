<section>
    <label>
        <input type="file">
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