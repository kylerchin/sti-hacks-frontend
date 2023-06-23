<script lang="ts">
	import Header from '../header.svelte';

	let sidebarItems = [
		{ name: 'Dashboard', icon: 'home', page: '/dashboard' },
		{ name: 'Form', icon: 'user', page: '/patient' },
		{ name: 'Messaging', icon: 'send', page: '/messaging' }
	];
	3;
	let activeItem = sidebarItems[0];

	function navigateTo(page) {
		window.location.href = page;
	}

	let patientItems = [
		{
			name: 'Bobby Brown',
			prob: '81%',
			status: 'Completed'
		},
		{
			name: 'Wendy William',
			prob: '56%',
			status: 'Pendng'
		},
		{
			name: 'Abby Cadabby',
			prob: '10%',
			status: 'Pending'
		}
	];
</script>

<Header />
<div class="body">
	<div class="sidebar">
		{#each sidebarItems as item}
			<div class="sidebar-item" on:click={() => navigateTo(item.page)}>
				<img class="icon" src={`/${item.icon}.svg`} alt={item.icon} />
				<span>{item.name}</span>
			</div>
		{/each}
	</div>

	<div class="middle">
		<div class="header">
			<div class="header-text">
				<h1>Welcome Physician</h1>
			</div>
		</div>

		<div class="patients-box">
			<div class="patients">
				{#each patientItems as patient}
					<div class="patient-box">
						<h4>{patient.name}</h4>
						<p>{patient.prob}</p>
						<p>{patient.status}</p>
					</div>
				{/each}
			</div>
		</div>
	</div>

	<div class="right">
		<div class="profile-box">
			<div class="profile">
				<h2>My Profile</h2>
			</div>
			<div class="profile-picture">
				<img src={`/ww.jpg`} alt="avatar" />
			</div>
		</div>
	</div>
</div>

<style>
	.body {
		display: flex;
		flex-direction: row;
		background-color: #1a3037;
	}

	.sidebar {
		width: 250px;
		height: 700px;
		background-color: #e7ecef;
		padding: 20px;
		margin-left: 20px;
		margin-top: 50px;
		border-radius: 10px;
	}

	.sidebar-item {
		display: flex;
		align-items: center;
		margin-bottom: 10px;
		cursor: pointer;
		padding: 5px;
	}

	.sidebar-item:hover {
		background-color: #e7ecef;
	}

	.icon {
		width: 25px;
		height: 25px;

		margin-right: 10px;
	}

	.header-box {
		font-family: 'IBM Plex Sans';
		justify-content: center;
		padding-top: 70px;
		padding-left: 300px;
		background-color: #e7ecef;
		border-radius: 10px;
		margin-top: 60px;
		margin-left: 60px;
	}

	.header {
		font-family: 'IBM Plex Sans';
		margin-left: 50px;
		margin-top: 50px;
		justify-content: center;
		background-color: #e7ecef;
		width: 900px;
		height: 100px;
		border-radius: 10px;
	}

	.header-text {
		text-align: left;
		margin-left: 20px;
		margin-top: 20px;
	}

	h1 {
		justify-content: center;
	}

	.middle {
		display: flex;
		flex-direction: column;
	}

	.patients {
		justify-content: center;
		padding-top: 70px;
		padding-left: 300px;
		background-color: #e7ecef;
		border-radius: 10px;
		margin-top: 60px;
		margin-left: 50px;
		width: -400px;
		height: 380px;
	}

	.patient-box {
		color: white;
		padding-left: 20px;
		padding-top: 15px;
		background-color: #446e70;
		height: 100px;
		border-radius: 10px;
		margin-left: -260px;
		margin-top: -30px;
		margin-right: 50px;
		margin-bottom: 45px;
	}

	.profile-box {
		width: 300px;
		height: 670px;
		background-color: #e7ecef;
		padding: 20px;
		margin-left: 520px;
		margin-top: 20px;
		border-radius: 10px;
	}

	.profile-picture {
		width: 150px;
		height: 150px;
		border-radius: 10px;
		object-fit: cover;
	}

	h1 {
		display: inline-block;
		text-align: center;
		font-family: 'IBM Plex Sans';
		font-size: 40px;
	}

	h2 {
		display: inline-block;
		text-align: center;
		font-family: 'IBM Plex Sans';
		font-size: 30px;
	}
</style>
