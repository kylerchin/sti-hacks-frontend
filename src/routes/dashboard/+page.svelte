<script lang="ts">

    /*import Header from './header.svelte';
	import Footer from './footer.svelte'; */

    let sidebarItems = [
        { name: 'Dashboard', icon: 'home', page: '/dashboard' },
        { name: 'Account', icon: 'user', page: '/patient' },
        { name: 'Map', icon: 'map-pin', page: '/map' },
        { name: 'Mesaging', icon: 'send', page: '/messaging'}
    ];
    
    let activeItem = sidebarItems[0];

    function navigateTo(page) {
        window.location.href = page;
    }

    let patientItems = [
        {
            pfr: 'path',
            name: 'Patient',
            desc: 'Whatever',
            prob: '80%'
        }
    ];

</script>

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
        <div class="header-box">
            <div class="header">
                <h1>Welcome Physician</h1>
            </div>
        </div>
        
        <div class="patients-box">
            <div class="patients">
                {#each patientItems as patient}
                    <div class="patient-box">
                        <h4>{patient.name}</h4>
                        <p>{patient.desc}</p>
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
                <img src={`/ww.jpg`} alt="avatar"/>
            </div>
        </div>
    </div>
</div>


<style>
    .body {
        display:flex;
        flex-direction: row;
        background-color: #446E70;
    }

    .sidebar {
        width: 160px;
        height: 700px;
        background-color: #f0f0f0;
        padding: 20px;
        margin-left: 20px;
        margin-top: 20px;
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
        background-color: #e0e0e0;
    }

    .icon {
        width: 25px;
        height: 25px;

        margin-right: 10px;
    }

    .middle {
        display: flex;
        flex-direction: column;
    }

    .header-box {
        justify-content: center;
        padding-top: 70px;
        padding-left: 300px;
        background-color: #f0f0f0;
        border-radius: 10px;
        margin-top: 60px;
        margin-left: 60px;
    }

    .header {
        justify-content: center;
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
        background-color: #e0e0e0;
        border-radius: 10px;
        margin-top: 60px;
        margin-left: 60px;
        width: -400px;
        height: 380px;
    }

    .patient-box {
        justify-content: center;
        background-color: #f0f0f0;
        width: px;
        height: 100px;
        border-radius: 10px;
    }

    .profile-box {
        width: 300px;
        height: 670px;
        background-color: #f0f0f0;
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