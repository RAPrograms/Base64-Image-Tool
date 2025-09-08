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
        display: flex;
        gap: 5px;
        align-items: center;
        height: 30px;
        font-size: 20px;

        & > :global(svg){
            height: 100%;
            aspect-ratio: 1/1;
        }

    }
</style>