<script lang="ts">
    const owner = import.meta.env.VITE_PROJECT_OWNER
</script>

<header>
    <h1>Base64 Image Tool</h1>
    <div>By {owner}</div>
</header>

<style lang="scss">
    header{
        padding: 10px;

        & > h1{
            line-height: 20px;
            font-size: x-large;
        }

        & > div{
            font-style: italic;
            font-size: small;
        }
    }
</style>