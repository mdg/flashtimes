<script>
	export let i;
	export let x;
	export let y;
	export let z;
	export let unknown;
	export let show_answer = false;
	
	var display_x = x;
	var display_y = y;
	var display_z = z;

	$: if (!show_answer) {
		switch (unknown) {
			case 0:
				display_x = "?";
				display_y = y;
				display_z = z;
				break;
			case 1:
				display_x = x;
				display_y = "?";
				display_z = z;
				break;
			case 2:
				display_x = x;
				display_y = y;
				display_z = "?";
				break;
		}
	} else {
		display_x = x;
		display_y = y;
		display_z = z;
	}
</script>

<span>
  <strong>{i}.</strong>
</span>

&nbsp;&nbsp;&nbsp;

<span>
  {display_x}
</span>

<span>
  <strong>x</strong>
</span>

{display_y} = {display_z}
