<script>
	import Sentence from "./Sentence.svelte";
	import InputText from "./InputText.svelte";

	let make = "Apple";
	let model = "iPhone";
	let memory = "64GB";

	let half = true;
	let hero = true;

	let showcard1 = 1;
	let showcard2 = 0;
	let showcard3 = 0;
	let hideButton1 = 0;
	let hideButton2 = 0;
	let hideButton3 = 0;

	let firstname, lastname, email;
	let dob, phone, postcode;
	let imei;

	$: card1isFilled =
		firstname !== "" &&
		lastname !== "" &&
		email !== "" &&
		phone !== ""; /* is false if any are false*/
	$: card2isFilled = dob !== "" && postcode !== "";
	$: card3isFilled = imei !== "" && imei !== "";

	$: hideButton1 = 0;

	let card1style, card2style, card3style;
	$: if (card1isFilled && hideButton1) {
		card1style = "collapsed";
	}
	$: if (card2isFilled && hideButton2) {
		card2style = "collapsed";
	}
	$: if (card3isFilled && hideButton3) {
		card3style = "collapsed";
	}
</script>

<main>
	<div class="form">
		<Sentence stage={2} {make} {model} {memory} />

		<!-- <InputSelectList /> -->

		<fieldset
			style="visibility:{showcard1 ? 'visible' : 'hidden'}"
			class={card1style}
		>
			<InputText bind:value={firstname} {half} {hero} label="First name" />
			<InputText bind:value={lastname} {half} {hero} label="Last name" />
			<InputText bind:value={email} label="Email" format="email" />
			<InputText bind:value={phone} label="Phone" />
			<button
				hidden={!card1isFilled || hideButton1}
				on:click={() => {
					showcard2 = 1;
					hideButton1 = 1;
					//mainStyle = "collapsed";
				}}
				class="wide">OKish</button
			>
		</fieldset>
		<fieldset
			style="visibility:{showcard2 ? 'visible' : 'hidden'}"
			class={card2style}
		>
			<InputText bind:value={dob} label="Date of Birth" />

			<InputText bind:value={postcode} label="Postcode" format="postcode" />
			<button
				hidden={!card2isFilled || hideButton2}
				on:click={() => {
					showcard3 = 1;
					hideButton2 = 1;
				}}
				class="wide">OKish</button
			>
		</fieldset>

		<fieldset
			style="visibility:{showcard3 ? 'visible' : 'hidden'}"
			class={card3style}
		>
			<InputText bind:value={imei} label="IMEI number" />

			<button
				hidden={!card3isFilled || hideButton3}
				on:click={() => {
					showcard2 = 1;
					hideButton2 = 1;
				}}
				class="wide">OKish</button
			>
		</fieldset>
	</div>
</main>

<style>
</style>
