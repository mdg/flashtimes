<script>
    import FlashForward from './FlashForward.svelte';
    import Launch from './Launch.svelte';

	let name = 'Third Grader';

    let launched = false;

    let num_problems = 100;

    function handle_launch(e)
    {
        launch = false;
    }
</script>

<style>
</style>

<h1>Hi {name}!</h1>

{#if launched}
<FlashForward
    upper=11
    {num_problems}
    />
{:else}
<Launch
    bind:launched={launched}
    bind:num_problems={num_problems}
    />
{/if}
