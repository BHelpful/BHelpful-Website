<script>
  import bhelpfulLogo from './assets/bhelpful.svg';
  import ProjectList from './lib/ProjectList.svelte';
  import Socials from './lib/Socials.svelte';

  const currentYear = new Date().getFullYear();
</script>

<style>
  img {
    height: 100px;
  }

  h1 {
    font-size: 3.2em;
    line-height: 0.3;
  }

  h1 + p {
    font-size: 1.2em;
    line-height: 1.5;
    font-style: italic;
    margin: auto;
    margin-bottom: 70px;
    max-width: 450px;
  }

  .components {
    display: flex;
    flex-direction: column;
    gap: 100px;
  }

  #footer {
    color: #ffffff88;
    margin: 0 auto;
  }

  #footer span {
    display: block;
    color: #ffffff55;
    font-size: 16px;
  }
</style>

<main>
  <img src={bhelpfulLogo} class="logo bhelpful" alt="BHelpful Logo" />
  <h1>BHelpful</h1>
  <p>We are developing apps/websites, that we think will be helpful for you, your sanity, and your everyday.</p>

  <div class="components">
    <ProjectList />
    <Socials />
  </div>

  <p id="footer">
    Copyright BHelpful {currentYear} - All Rights Reserved
    <span>The Invertocat Logo is a trademark of GitHub, Inc.</span>
    <span>The in Logo is a trademark of LinkedIn Corporation.</span>
  </p>
</main>
