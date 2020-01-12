<script>
  import FlashCard from './FlashCard.svelte';
	import { fade, slide } from 'svelte/transition';

	let name = 'Third Grader';
	let random_facts = [];
	let squares = [];
	for (var x=2; x<12; x++) {
  	for (var y=2; y<12; y++) {
			const product = x * y;
			random_facts.push([Math.random(), x, y, product, 0]);
			random_facts.push([Math.random(), x, y, product, 1]);
			random_facts.push([Math.random(), x, y, product, 2]);
		}
	}
	random_facts.sort()
	let facts = random_facts.map(function(f) {
	  f.splice(0, 1);
	  return f;
	});
	
	let i = 0;
	let xi = facts[i][0];
	let yi = facts[i][1];
	let zi = facts[i][2];
	$: ifact = facts[i];
	$: j = Math.max(0, i - 1);
	$: jfact = facts[j];
	
	let answer_display = "none";
	let prompt_display = "";
	
	function show_answer() {
		i = i + 1;
		console.log("i = " + i);
		prompt_display = "none";
		answer_display = "";
	}

	function show_next() {
		i = i + 1;
		prompt_display = "none";
		answer_display = "none";
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
		font-size: 18pt;
	}
	button {
		width: 200px;
	}
</style>

<svelte:window on:keydown={handle_keydown}/>

<h1>Hello {name}!</h1>
{#if prompt_display === ""}
<p id="fact_sentence" style="display: {prompt_display};" transition:fade="{{ duration: 1000 }}">
	<FlashCard
					 i={i + 1}
					 x={ifact[0]}
					 y={ifact[1]}
					 z={ifact[2]}
					 unknown={ifact[3]}
					 />
</p>
{/if}
<p id="last_fact">
	<FlashCard
					 {i}
					 x={facts[j][0]}
					 y={facts[j][1]}
					 z={facts[j][2]}
					 unknown={facts[j][3]}
					 show_answer={true}
					 />
</p>

<p id=next_button>
	<button on:click={handle_show_next}>
	  next fact
  </button>
</p>
<p>
	{#each facts as fact, k}
	  {#if i == k}
	    <div transition:slide="{{ duration: 1000 }}">
	  	<FlashCard
							 i={k}
							 x={facts[k][0]}
						   y={facts[k][1]}
							 z={facts[k][2]}
							 unknown={facts[k][3]}
							 show_answer={true}
							 />
			</div>
	  {/if}
	{/each}
</p>
