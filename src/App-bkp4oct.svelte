<script>
	import Sentence from "./Sentence.svelte";
	import InputText from "./InputText.svelte";

	let make = "Apple";
	let model = "iPhone";
	let memory = "64GB";
	let half = true;
	let hero = true;
	let card1, card2;
	let button1 = true,
		button2 = false;
	$: button1hide = button1;
	let showButton1 = false;

	let email;
	$: if (email !== undefined) {
		showButton1 = true;
	}
</script>

<main>
	<div class="form">
		<Sentence stage={2} {make} {model} {memory} />

		<!-- <InputSelectList /> -->

		<fieldset class={card1}>
			<InputText {half} {hero} label="First name" />
			<InputText {half} {hero} label="Last name" format="email" />
			<InputText label="Email" format="email" />
			{#if showButton1}
				<button on:click={() => (card1 = "closed")} class="wide">OKish</button>
			{/if}
		</fieldset>
		<fieldset>
			<InputText label="Date of Birth" />
			<InputText label="Phone" />
			<InputText label="Postcode" format="postcode" />
			<button {button2} on:click={() => (email = "e")} class="wide"
				>OKish</button
			>
		</fieldset>
	</div>
</main>

<style>
</style>
