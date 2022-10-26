<script>
    import { socials } from '../data/socials.json';
    
    socials.map(socials => {
        socials.logo = new URL(socials.logo, import.meta.url);
    });
</script>

<style>
    h2 {
        line-height: 0.3em;
        margin: 0;
    }

    .list {
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        gap: 20px;
        margin-block: 20px;
    }

    .card {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        padding: 1em;
        border-radius: 1em;
        width: 200px;
        transition: all 0.3s 0s ease-in-out;
    }

    .card:hover {
        background-color: #272727;
        cursor: pointer;
        transition: all 0.3s 0s ease-in-out;
    }

    .logo {
        height: 5em;
        padding: 0 1.5em;
        will-change: filter;
    }

</style>

<div id="socials">
    <h2>Find us on:</h2>
    <div class="list">
        {#each socials as social}
            <div class="card" on:click="{() => window.open(social.url, '_blank')}">
                <p>{social.description}</p>
                <img src={social.logo} class="logo" alt="Visit" />
                <h3>{social.name}</h3>
            </div>
        {/each}
    </div>
</div>