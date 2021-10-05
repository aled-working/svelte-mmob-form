<script>
	export let make, model, memory;

	let first = "Find me phone insurance for ",
		second = make ? make : "",
		third = model ? model : "",
		fourth = third ? "with" : "",
		fifth = memory ? `(${memory})` : "";
</script>

<h1>{first} {second} {third} {fourth} {fifth}</h1>

<style>
</style>
