<script>
	import { fade } from 'svelte/transition';

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
        position: relative;
		width: 40px;
        text-align: center;
	}

	span.factor {
        width: 100%;
        position: absolute;
        top: 0px;
        left: 0px;
        display: inline-block;
        text-align: center;
	}

    span.question-mark {
        color: green;
        font-weight: bold;
    }
</style>

<span class="problem_number">
  <strong>{i}.</strong>
</span>

<span class="number">&nbsp;
{#if unknown === 0 && !show_answer}
<span class="factor question-mark"
    out:fade|local="{{ duration: 250 }}"
    >?</span>
{:else}
<span class="factor"
    in:fade|local="{{ delay: 250, duration: 250 }}"
    >
  {x}
</span>
{/if}
</span>

x

<span class="number">&nbsp;
{#if unknown === 1 && !show_answer}
<span class="factor question-mark"
    out:fade|local="{{ duration: 250 }}"
    >?</span>
{:else}
<span class="factor"
    in:fade|local="{{ delay: 250, duration: 250 }}"
    >
{y}
</span>
{/if}
</span>

=

<span class="number">&nbsp;
{#if unknown === 2 && !show_answer}
<span class="factor question-mark"
    out:fade|local="{{ duration: 250 }}"
    >?</span>
{:else}
<span class="factor"
    in:fade|local="{{ delay: 250, duration: 250 }}"
    >
{z}
</span>
{/if}
</span>
