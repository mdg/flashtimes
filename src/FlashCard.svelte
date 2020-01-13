<script>
	export let i;
	export let x;
	export let y;
	export let z;
	export let unknown;
	export let show_answer = false;
</script>

<style>
	span.number {
        display: inline-block;
		width: 40px;
        text-align: center;
	}
</style>

<span style="display: inline-block; width: 80;">
  <strong>{i}.</strong>
</span>

{#if unknown === 0}
<span class=number>?</span>
{:else}
<span class=number>
  {x}
</span>
{/if}

<strong>x</strong>

{#if unknown === 1}
<span class=number>?</span>
{:else}
<span class=number>
{y}
</span>
{/if}

=

{#if unknown === 2}
<span class=number>?</span>
{:else}
<span class=number>
{z}
</span>
{/if}
