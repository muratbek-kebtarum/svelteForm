<script>
    export let loading = false;
</script>

{#if loading}
    <div class="loading-overlay">
        <div class="loader">Sending...</div>
    </div>
{/if}

<style>
    .loading-overlay {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background-color: rgba(0, 0, 0, 0.7);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 9999;
    }

    .loader {
        color: white;
        font-size: 2rem;
    }
</style>
