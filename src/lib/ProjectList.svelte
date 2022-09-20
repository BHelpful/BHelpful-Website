<script>
  import mealtimeLogo from '../assets/mealtime.svg';
  import bhelpfulLogo from '../assets/bhelpful.svg';
  import undefinedLogo from '../assets/undefined.svg';
  import closedSourceLogo from '../assets/closedSource.svg';
  import invertocatLogo from '../assets/invertocat.svg';
  // Get invertocat logo
  const projects = [
    {
      name: 'MealTime',
      description: 'A meal planning app that helps you plan and discover new recipes.\nBuilt with NestJS and angular.\n(Previously known as MealPlanr)',
      logo: mealtimeLogo,
      url: 'https://mealtime.bhelpful.net',
      github: 'https://github.com/bhelpful/mealtime',
      mainDevs: ['@andreasgdp', '@toeffe3'],
      openSource: true,
      status: 'InDev',
    },
    {
      name: 'BHelpful Website',
      description: 'The website you are currently on. Built with Svelte',
      logo: bhelpfulLogo,
      url: 'https://bhelpful.net',
      github: 'https://github.com/bhelpful/bhelpful-website',
      mainDevs: ['@toeffe3'],
      openSource: true,
      status: 'Published',
    },
    {
      name: 'Organizer',
      description: 'An app for IOS and Android that can help you organize and keep count on stuff in your house.',
      logo: undefinedLogo,
      url: undefined,
      github: undefined,
      mainDevs: ['@BareMaxx', '@alex123a'],
      openSource: false,
      status: 'Planning',
    }
  ];
</script>

<style>
  #projects {
    width: calc(100vw - 200px);
    margin: auto;
  }
  
  .list {
    overflow-x: visible;
    display: flex;
    text-align: left;
    flex-direction: row;
    flex-wrap: nowrap;
    gap: 40px;
    scroll-snap-type: x mandatory;
    padding: 20px;
    overflow-x: scroll;
    margin: auto;
    width: min-content;
    max-width: 100%;
  }
  
  .card {
    margin: 0 auto;
    min-width: 250px;
    display: grid;
    grid-template-areas: "logo header"
                         "description description"
                         "github devs"
                         "github devslist";
    grid-template-columns: 80px 180px;
    grid-template-rows: 50px 125px 1em 70px;
    grid-gap: 5px;
    border: 3px solid #ffffff;
    border-radius: 25px 25px 25px 0px;
    padding: 25px;
    transition: all .3s ease-in-out;
    position: relative;
    overflow: hidden;
    scroll-snap-align: center;
  }

  @media (max-width: 1200px) { 
    .card:first-child {
      margin-left: calc(100% / 3);
    }
    
    .card:last-child {
      margin-right: calc(100% / 3);
    }
  }

  .card:hover {
    transform: scale(1.08);
    transition: all .3s 0s ease-in-out;
    cursor: pointer;
  }

  /* Banner across the top right side */
  #status {
    position: absolute;
    transform: translate(-50%, -50%) rotate(45deg) translate(-5px, 5px);
    background: #ffffff;
    margin: 0;
    color: #2c2d2b;
    font-weight: bold;
    top: 38px;
    right: -120px;
    height: 35px;
    width: 150px;
    text-align: center;
    line-height: 30px;
  }

  .logo {
    grid-area: logo;
    height: 60px;
    margin: 0 auto;
  }

  .header {
    grid-area: header;
    text-decoration: none;
    color: inherit;
  }

  .description {
    grid-area: description;
  }

  .github {
    grid-area: github;
    margin: 0 auto;
    text-decoration: none;
    text-align: center;
    color: inherit;
  }

  .github img {
    height: 40px;
    margin: 0 5px;
  }

  .github p {
    margin: 0;
  }

  .devs {
    grid-area: devs;
    margin: 0 auto;
  }

  .devslist {
    grid-area: devslist;
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
    flex-wrap: wrap;
    margin: 0 15px;
    position: relative;
    height: min-content;
  }

  .devslist a {
    margin: 0 5px;
  }
  
</style>

<div id="projects">
  <h2>Projects:</h2>
  <div class="list">
    {#each projects as project}
      <!-- card should open site when clicked -->
      <div class="card" on:click={() => window.open(project.url, '_blank')}>
        <p id="status">{project.status}</p>
        <img src={project.logo} class="logo" alt="Visit" />
        <h3 class="header">{project.name}</h3>
        <!-- Make sure that \n is interplolated as line breaks -->
        <p class="description">
        {#each project.description.split('\n') as line}
          {line}<br/>
        {/each}
        </p>
        <!-- open or close sourced -->
        {#if project.openSource}
          <a class="github" href={project.github} on:click={e => e.stopPropagation()}>
            <img src={invertocatLogo} alt="Github" />
            <p>Code</p>
          </a>
        {:else}
          <a class="github" href={""}>
            <img src={closedSourceLogo} alt="" />
            <p>Closed Source</p>
          </a>
        {/if}
        <p class="devs">Developers</p>
        <p class="devslist">
          {#each project.mainDevs as dev}
            <a href={`https://github.com/${dev.slice(1)}`} target="_blank" rel="noopener noreferrer">{dev}</a>
          {/each}
        </p>
      </div>
    {/each}
  </div>
</div>
