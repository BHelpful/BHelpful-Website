<script>
  import closedSourceLogo from '../assets/closedSource.svg';
  import invertocatLogo from '../assets/invertocat.svg';
  import { projects } from '../data/projects.json';

  projects.map(project => {
    project.logo = new URL(project.logo, import.meta.url);
  });

  document.documentElement.style.setProperty('--projects', `${Object.keys(projects).length}`);

  const isHacktober = () => (new Date()).getMonth() === 9;
</script>

<style>
  #projects {
    width: calc(100vw - 4rem);
  }
  
  .list {
    margin: auto;
    display: flex;
    text-align: left;
    flex-direction: row;
    flex-wrap: nowrap;
    gap: 40px;
    scroll-snap-type: x mandatory;
    padding: 20px;
    overflow-x: scroll;
    width: auto;
    max-width: calc(400px * var(--projects));
  }
  
  .card {
    margin: 0 auto;
    width: 280px;
    min-width: 280px;
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
      margin-left: calc(100% / var(--projects));
    }
    
    .card:last-child {
      margin-right: calc(100% / var(--projects));
    }
  }

  .card:hover {
    transform: scale(1.08);
    transition: all .3s 0s ease-in-out;
    cursor: pointer;
  }

  .card.hacktober {
    /* Blue purple gradient border */
    background: linear-gradient(45deg, rgba(1,0,158,1) 0%, rgba(40,40,190,1) 24%, rgba(134,0,255,1) 100%)
  }
  .card.hacktober::after {
    content: 'Open for Hacktoberfest contributions';
    position: absolute;
    bottom: 5px;
    width: 100%;
    text-align: center;
    font-weight: bold;
    color: #db6eff;
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
      <div class="card {project.hacktober && isHacktober() ? 'hacktober' : ''}" on:click={() => window.open(project.url, '_blank')}>
        <p id="status">{project.status}</p>
        <img src={project.logo} class="logo" alt="Logo" />
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
