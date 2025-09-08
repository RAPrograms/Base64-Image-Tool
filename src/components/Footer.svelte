<script lang="ts">
    import github_logo from "/src/assets/github-logo.svg?raw"

    const repo_url = import.meta.env.VITE_REPO_URL
</script>

<footer>
    { @html github_logo }
    <b>
        Source Code on 
        <a href={repo_url}>Github</a>
    </b>
</footer>

<style lang="scss">
    footer{
        justify-content: center;
        align-items: center;
        margin-bottom: 10px;
        font-size: 15px;
        display: flex;
        padding: 3px;
        height: 30px;
        gap: 5px;

        & > :global(svg){
            height: 100%;
            aspect-ratio: 1/1;
        }
    }
</style>