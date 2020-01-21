<script>
	import FlashCard from './FlashCard.svelte';
	import { slide } from 'svelte/transition';

	export let upper = 11;
	export let num_problems = 100;

	let random_facts = [];
	let squares = [];
	for (var x=2; x<=upper; x++) {
		for (var y=2; y<=upper; y++) {
			const product = x * y;
			random_facts.push([Math.random(), x, y, product, 0]);
			random_facts.push([Math.random(), x, y, product, 1]);
			random_facts.push([Math.random(), x, y, product, 2]);
		}
	}
	random_facts.sort();
	let facts = random_facts.splice(0, num_problems).map(function(f) {
	  f.splice(0, 1);
	  return f;
	});

    let prompt_index = 0;
    let answer_index = -1;

	function show_next() {
        answer_index += 1;
        prompt_index += 1;
	}

	function handle_show_next(event) {
		show_next();
	}

	function handle_keydown(event) {
		if (String.fromCharCode(event.keyCode) === " ") {
			show_next();
		} else {
	    // answer = String.fromCharCode(event.keyCode);
		}
	}
</script>

<style>
	p {
		font-size: 30pt;
	}
	button {
		width: 200px;
	}
</style>

<svelte:window on:keypress={handle_keydown}/>

<p>
    {#if answer_index == -1}
      <div
        transition:slide="{{ delay: 500, duration: 500 }}"
        style="padding: 10px;"
        >&nbsp;</div>
    {/if}
	{#each facts as fact, k}
	  {#if k === prompt_index || k === answer_index}
        <div
            transition:slide="{{ delay: 500, duration: 500 }}"
            style="padding: 10px;"
            >
        <FlashCard
							 i={k + 1}
							 x={facts[k][0]}
						   y={facts[k][1]}
							 z={facts[k][2]}
							 unknown={facts[k][3]}
							 show_answer={k === answer_index}
							 />
        </div>
	  {/if}
	{/each}
</p>
<p id=next_button>
	<button on:click={handle_show_next}>
	  next fact
  </button>
</p>
