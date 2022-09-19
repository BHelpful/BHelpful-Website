<script>
  import mealtimeLogo from '../assets/mealtime.svg';
  // Get invertocat logo
  const githubIcon = 'https://github.githubassets.com/favicons/favicon-dark.svg';
  const projects = [
    {
      name: 'MealTime',
      description: 'A meal planning app that helps you plan and discover new recipes.',
      logo: mealtimeLogo,
      url: 'mealtime.bhelpful.net',
      github: 'github.com/bhelpful/mealtime',
      mainDevs: ['@andreasgdp', '@toeffe3'],
      openSource: true,
      status: 'In Development',
    },
    
  ];
</script>

<style>
  .list {
    display: flex;
    text-align: left;
    flex-direction: row;
    flex-wrap: nowrap;
    overflow-x: scroll;
    gap: 50px;
  }
  
  .card {
    margin: 0 auto;
    min-width: 200px;
    max-width: 300px;
    display: grid;
    grid-template-areas: "icon header"
                         "description description"
                         "github devs"
                         "github devslist";
    grid-template-columns: 1fr 4fr;
    grid-template-rows: 50px max-content 1em 70px;
    grid-gap: 1em;
    border: 3px solid #fff;
    border-radius: 25px 25px 25px 0px;
    padding: 25px;
  }

  .icon {
    grid-area: icon;
  }

  .icon img {
    height: 60px;
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
    justify-content: center;
    align-items: center;
    display: flex;
    text-decoration: none;
    flex-direction: column;
    color: inherit;
  }

  
  .devs {
    grid-area: devs;
    justify-content: center;
    align-items: center;
    display: flex;
  }

  .devslist {
    grid-area: devslist;
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
    flex-wrap: wrap;
    margin: 0;
    position: relative;
  }

  .devslist a {
    margin: 5px;
  }
  
</style>

<div id="projects">
  <h2>Projects:</h2>
  <div class="list">
    {#each projects as project}
      <div class="card">
        <a href={project.url} target="_blank" class="icon">
          <img src={project.logo} class="logo" alt="Visit" />
        </a>
        <a href={project.url} target="_blank" class="header">
          <h3>{project.name}</h3>
        </a>
        <p class="description">{project.description}</p>
        <a href={project.github} target="_blank" class="github">
          <img src={githubIcon} class="logo" alt="Github" />
          <p>Code</p>
        </a>
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
