<script>
    import invertocatLogo from '../assets/invertocat-white.svg';
    import { socials } from '../data/data.json';
    socials.map(social => {
        switch (social.name) {
            case 'GitHub':
                social.logo = invertocatLogo;
                break;
            case 'LinkedIn':
                social.logo = "https://cdn.worldvectorlogo.com/logos/linkedin-icon-2.svg";
                break;
            default:
                social.logo = invertocatLogo;
        }
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