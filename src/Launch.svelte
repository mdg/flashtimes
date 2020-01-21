<script>
    export let launched = false;
    export let op_add = false;
    export let op_sub = false;
    export let op_mult = true;
    export let op_div = false;
    export let num_problems = 100;

    function toggle_add()
    {
        op_add = !op_add;
    }

    function handle_launch(e)
    {
        launched = true;
    }
</script>

<style>
    span.problem_number {
        display: inline-block;
        width: 60px;
        font-weight: bold;
    }

	span.number {
        display: inline-block;
        position: relative;
		width: 55px;
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

    span.unknown {
        color: green;
        font-weight: bold;
    }

    button.operation {
        width: 50px;
    }

    button#go_button {
        width: 80px;
    }

    input {
        width: 100px;
    }
</style>

<p>
    <button class="operation" on:click={toggle_add}>+</button>
    {op_add}
    &nbsp;
    <button class="operation" on:click={handle_launch}>-</button>
    &nbsp;
    <button class="operation" on:click={handle_launch}>x</button>
    &nbsp;
    <button class="operation" on:click={handle_launch}>÷</button>
</p>

<p>
    # of Problems: <input bind:value={num_problems} />
</p>

<p>
	<button id=go_button on:click={handle_launch}>
	  go
  </button>
</p>
