<script>
    import FlashForward from './FlashForward.svelte';
    import Launch from './Launch.svelte';

	let name = 'Third Grader';

    let launched = false;

    let num_items = true;

    function handle_launch(e)
    {
        launch = false;
    }
</script>

<style>
</style>

<h1>Hi {name}!</h1>

{#if launched}
<FlashForward upper=11 />
{:else}
<Launch bind:launched={launched}/>
{/if}
