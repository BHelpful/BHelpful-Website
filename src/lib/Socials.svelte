<script>
    import invertocatLogo from '../assets/invertocat-white.svg';
    // Get social logos
    const socials = [
        {
            name: 'Github',
            description: 'Looking to contribute?',
            logo: invertocatLogo,
            url: 'https://github.com/bhelpful',
        },
        {
            name: 'LinkedIn',
            description: 'Connect with us',
            logo: 'https://cdn.worldvectorlogo.com/logos/linkedin-icon-2.svg',
            url: 'https://linkedin.com/company/bhelpful',
        },
    ];
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
    }

    .card {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        margin: 1em;
        padding: 1em;
        border-radius: 1em;
    }

    .card a {
        text-decoration: none;
        color: inherit;
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
            <div class="card">
                <a href={social.url} target="_blank">
                <p>{social.description}</p>
                    <img src={social.logo} class="logo" alt="Visit" />
                    <h3>{social.name}</h3>
                </a>
            </div>
        {/each}
    </div>
</div>