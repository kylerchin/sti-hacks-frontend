<script lang="ts">
	import Header from '../header.svelte';
	import { onMount } from 'svelte';

	let textBoxes: string[] = []; // Array to store the values of text boxes

	onMount(() => {
		// Initialize the array with empty values for the text boxes
		textBoxes = Array(15).fill('');
	});

	let values: string[] = [
		'First Name*',
		'Last Name*',
		'Age*',
		'Sex*',
		'Ethnicity*',
		'Region*',
		'Address*',
		'Wealth Index*',
		'Education*',
		'Working Status*',
		'Marital Status*',
		'Internet Access*',
		'Alcohol Consumption*',
		'Age at First Sex*',
		'Connections',
		'DIS Referral'
	];

	let keys: string[] = [
		'first',
		'last',
		'age',
		'sex',
		'ethnicity',
		'region',
		'address',
		'wealth',
		'education',
		'working_status',
		'marital',
		'internet',
		'alcohol',
		'age_of_first',
		'connections',
		'dis_referral'
	];

	function saveData() {
		var data: { [key: string]: string } = {};

		keys.forEach((key, index) => {
			data[key] = textBoxes[index];
		});

		console.log('data to send', data);

		fetch('https://stibackend.kylerchin.com/addpatient', {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			},
			body: JSON.stringify(data)
		})
			.then((response) => response.json())
			.then((data) => {
				console.log(data);

				textBoxes = Array(15).fill('');
				window.location.href = '/dashboard';
			})
			.catch((error) => {
				console.error(error);
				// /alert('Error saving data');
			});
	}
</script>

<div class="min-h-screen bruzbackground">
	<Header />
	<div class="container">
		<div class="left-box">
			<h1 class="text-white px-2 py-1 text-left">Patient Information</h1>
			<p class="text-white max-w-md text-left">
				Register your patient under your profile and refer your patient to a DIS in the community!
			</p>

			<div class="px-3 py-2 bg-[#446e70] text-white" id="import">Import from Epic</div>
		</div>

		<div class="text-white text-left" id="right-box">
			{#each textBoxes as textBox, index}
				<p class="text-lg">{values[index]}</p>
				<input type="text" bind:value={textBox} />
			{/each}
			<button class="register" on:click={saveData}>Register Patient</button>
		</div>
	</div>
</div>

<style>
	.container {
		display: flex;
	}

	#import {
		width: 150px;
		border-radius: 10px;
		margin-top: 30px;
		margin-left: 75px;
	}

	.left-box {
		flex: 1;
		padding: 50px;
		padding-left: 70px;
	}

	#right-box {
		flex: 1;
		overflow-y: auto;
		padding-top: 90px;
		padding-left: 50px;
		max-height: 100%;
		height: 90vh;
		display: flex;
		flex-direction: column;
		align-items: flex-start;
	}

	#right-box p {
		text-align: left;
		padding-left: 0px;
		padding-bottom: 5px;
	}

	h1 {
		padding-top: 75px;
		padding-left: 75px;
		font-family: 'IBM Plex Sans';
		font-size: 50px;
	}

	p {
		padding-top: 50px;
		padding-left: 75px;
		font-family: 'IBM Plex Sans';
	}

	.bruzbackground {
		text-align: left;
		background-color: #1f3942;
	}

	input[type='text'] {
		width: 400px;
		height: 50px;
		color: black;
		border-radius: 10px;
		font-family: 'IBM Plex Sans';
		font-size: 20px;
		padding-left: 10px;
		padding-top: 10px;
		padding-bottom: 10px;
	}

	.register {
		padding-top: 10px;
		padding: 10px 20px;
		background-color: #446e70;
		border-radius: 10px;
		color: white;
		font-size: 16px;
		margin-top: 50px;
		margin-bottom: 50px;
		margin-left: 122px;
	}
</style>
