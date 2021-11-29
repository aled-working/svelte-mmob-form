<script>
	export let label = "What label?";
	export let format;
	let current;
	let value = "";
	let filled;
	$: if (value !== "") {
		filled = true;
	}
</script>

<div
	class={`field 
            ${current ? " focused" : ""}
            ${filled ? " filled" : ""}
            ${format ? [format] : ""}
            `}
>
	<div class="question">{label}</div>
	<!-- <div class="sub">explanatory</div> -->
	<input
		type="text"
		bind:value
		on:focus={() => {
			current = true;
		}}
		on:blur={() => {
			current = false;
		}}
	/>
	<!-- <div class="prompt">prompt</div> -->
</div>

<style>
	.field {
		margin-bottom: 1rem;
		text-align: left;
		width: 48%;
		position: relative;
		display: inline-block;
	}

	.sub,
	label,
	.prompt {
		display: none;
	}
	input[type="text"] {
		/* border: 1px solid hsl(0, 0%, 90%); */
		border: none;
		background-color: hsl(0, 0%, 97%);
		width: 100%;
	}

	.question {
		position: relative;
		top: 1.9em;
		left: 0.4em;
		line-height: 1.5rem;
		pointer-events: none;
	}
	.focused .question/* ,
	.filled .question */ {
		top: 0em;
		font-size: 0.5em;
		/* text-align: right; */
	}
	/* show label on right after filling, to aid gradual collapse */
	.filled:not(.focused) .question {
		position: absolute;
		top: 1.1em;
		right: 0;
		text-align: right;
		font-size: 0.5em;
		/* hide until hover */
		visibility: hidden;
	}
	.filled:not(.focused):hover .question {
		visibility: visible;
	}

	.filled:not(.focused) input[type="text"] {
		border: none;
		font-weight: bold;
		border-bottom: 2px dotted hsl(0, 0%, 93%);
	}
	.filled:not(.focused):hover input[type="text"] {
		/* text-decoration: underline; */
		border-bottom: 2px dotted hsl(0, 0%, 67%);
	}
	.filled:not(.focused) {
		margin-bottom: 0;
	}
	.filled input[type="text"] {
		background: none;
		border: none;
	}
	.postcode input {
		text-transform: uppercase;
	}
</style>
