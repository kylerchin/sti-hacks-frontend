<script lang="ts">
	import Header from './header.svelte';
	import Footer from './footer.svelte';

	// Import the functions you need from the SDKs you need
	import { initializeApp } from 'firebase/app';
	import firebase from 'firebase/compat/app';
	import 'firebase/compat/auth';
	import { onMount } from 'svelte';
	// TODO: Add SDKs for Firebase products that you want to use
	// https://firebase.google.com/docs/web/setup#available-libraries

	// Your web app's Firebase configuration
	// For Firebase JS SDK v7.20.0 and later, measurementId is optional
	const firebaseConfig = {
		apiKey: 'AIzaSyAKUJIq6bjpUFSn9krJ9D2cQupN8biIyfw',
		authDomain: 'sti-hackathon.firebaseapp.com',
		projectId: 'sti-hackathon',
		storageBucket: 'sti-hackathon.appspot.com',
		messagingSenderId: '538088055127',
		appId: '1:538088055127:web:117ad676c60ab848ee9e12',
		measurementId: 'G-VL922YFEJ1'
	};

	onMount(() => {
		// Initialize Firebase
		const app = initializeApp(firebaseConfig);

		//const analytics = getAnalytics(app);

		let auth = firebase.auth();

		if (auth.currentUser) {
			// The user is already signed in.
		} else {
			// The user is not signed in.
		}
	});

	async function loginWithGoogle(bruz: string) {
		try {
			firebase.initializeApp(firebaseConfig);
			let auth = firebase.auth();
			// Initialize Firebase

			const provider = new firebase.auth.GoogleAuthProvider();

			await auth.signInWithPopup(provider);
			window.location.href = '/dashboard';
		} catch (e) {
			console.log(e);
		}
	}
</script>

<div class="min-h-screen bruzbackground bg-[#1f3942] flex flex-col">
	<Header />
	<div class="mx-4 mt-36 w-full" id="text-body">
		<div class="md:grid md:grid-cols-2 md:gap-x-2 w-full" id="body">
			<!-- <div class="hidden md:block">PUT THE GOD DAMN IMAGE HERE</div> -->
			<div class="">
				<h1 class="text-gray-50 px-2 py-1 max-w-md text-left">Rheia</h1>

				<h2 class="text-gray-50 px-2 py-3 max-w-md text-left">
					Rheia is a contact-tracing risk-assessment software for physicians and DIS to facilitate
					STI early prevention.
				</h2>

				<div class="flex flex-row gap-x-3 mt-1 ml-2 py-0.5">
					<button
						on:click={() => {
							loginWithGoogle('dis');
						}}
						class="px-3 py-2 bg-white text-black">Sign-in as DIS</button
					>
					<button
						on:click={() => {
							loginWithGoogle('provider');
						}}
						class="px-3 py-2 bg-[#446e70] text-white">Sign-in as provider</button
					>
				</div>
			</div>
		</div>
	</div>
	<Footer />
</div>

<style>
	h1 {
		font-family: 'IBM Plex Sans';
		font-size: 50px;
	}

	* {
		font-family: 'IBM Plex Sans';
	}

	#body {
		margin-left: 300px;
	}

	.bruzbackground {
		/*background: linear-gradient(rgba(0, 0, 0, 0.60), rgba(0, 0, 0, 0.60)), url("/dennis-mita-qmg0MidYviw-unsplash.jpg") no-repeat;*/
		background-size: 100%;
	}
</style>
