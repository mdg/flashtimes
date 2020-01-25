<script>
    export let launched = false;
    // export let op_add = false;
    // export let op_sub = false;
    export let op_mult = true;
    export let op_div = false;
    export let num_problems = 100;

    function toggle_op_add()
    {
        op_add = !op_add;
    }

    function toggle_op_mult()
    {
        op_mult = !op_mult;
    }

    function toggle_op_div()
    {
        op_div = !op_div;
    }

    function op_state_class(op_state)
    {
        return op_state ? "op_selected" : "op_unselected";
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
        width: 70px;
    }

    button.op_selected {
        background-color: #119911;
    }

    button.op_unselected {
        background-color: #b0b0b0;
    }

    input {
        width: 100px;
    }
</style>

<p>
    Which operations?
</p>
<p>
    <!--
    <button class="operation" on:click={toggle_op_add}>+</button>
    &nbsp;
    <button class="operation" on:click={toggle_op_sub}>-</button>
    &nbsp;
    -->
    <button class="operation {op_state_class(op_mult)}" on:click={toggle_op_mult}>x</button>
    &nbsp;
    <button class="operation {op_state_class(op_div)}" on:click={toggle_op_div}>÷</button>
</p>

<p>
    # of Problems? <input bind:value={num_problems} />
</p>

<p>
	<button id=go_button on:click={handle_launch}>
		&nbsp;
		go
		&nbsp;
	</button>
</p>
