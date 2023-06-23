<script lang="ts">
	import Header from './header.svelte';
	import Footer from './footer.svelte';
</script>

<div class="min-h-screen bruzbackground flex flex-col">
	<Header />
	<div class="mx-4 mt-36" id="text-body">
		<h1 class="text-gray-50 px-2 py-1 max-w-md text-left">Rheia</h1>

		<h2 class="text-gray-50 px-2 py-3 max-w-md text-left">
			Rheia is a contact-tracing risk-assessment software for physicians and DIS to facilitate STI
			early prevention.
		</h2>

		<div class="flex flex-row gap-x-7 mt-1 ml-2 py-0.5">
			<a href="/signin?who=dis"><div class="px-3 py-2 bg-white text-black">Sign-in as DIS</div></a>
			<a href="/signin?who=provider"
				><div class="px-3 py-2 bg-[#446e70] text-white">Sign-in as provider</div></a
			>
		</div>
	</div>
	<Footer />
</div>

<style>
	#text-body {
		padding-left: 1000px;
		padding-top: 70px;
		align-items: left;
		display: flex;
		flex-direction: column;
	}

	h1 {
		font-family: 'IBM Plex Sans';
		font-size: 50px;
	}

	* {
		font-family: 'IBM Plex Sans';
	}

	.bruzbackground {
		background-color: #1f3942;
		/*background: linear-gradient(rgba(0, 0, 0, 0.60), rgba(0, 0, 0, 0.60)), url("/dennis-mita-qmg0MidYviw-unsplash.jpg") no-repeat;*/
		background-size: 100%;
	}
</style>
