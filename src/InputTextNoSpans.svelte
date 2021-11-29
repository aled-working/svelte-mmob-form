<script>
	export let half = false;
	export let hero = false;
	export let label = "What label?";
	export let format;
	let current;
	export let value = "";
	let filled;
	$: if (value !== "") {
		filled = true;
	}
</script>

<!-- --------${current ? " focused" : ""}---- -->

<div
	class={`field 
            ${current ? " focused" : ""}
            ${filled ? " filled" : ""}
            ${half ? " half" : ""}
            ${hero ? " hero" : ""}
            ${format}
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
</style>
