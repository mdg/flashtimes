<script>
	export let i;
	export let x;
	export let y;
	export let z;
	export let unknown;
	export let show_answer = false;
</script>

<style>
    span.problem_number {
        display: inline-block;
        width: 40px;
        font-weight: bold;
    }

	span.number {
        display: inline-block;
		width: 40px;
        text-align: center;
	}

    span.question {
        color: green;
        font-weight: bold;
    }
</style>

<span class="problem_number">
  <strong>{i}.</strong>
</span>

{#if unknown === 0 && !show_answer}
<span class="number question">?</span>
{:else}
<span class=number>
  {x}
</span>
{/if}

x

{#if unknown === 1 && !show_answer}
<span class="number question">?</span>
{:else}
<span class=number>
{y}
</span>
{/if}

=

{#if unknown === 2 && !show_answer}
<span class="number question">?</span>
{:else}
<span class=number>
{z}
</span>
{/if}
