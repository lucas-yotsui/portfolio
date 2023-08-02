<script>
	import Chapters from "./Chapters.svelte";
  import Social from "./Social.svelte";

  let chapters = {
    current: 1,
    all: [
      {
        id: 1,
        name: "Projetos"
      },
      {
        id: 2,
        name: "Formação"
      }
    ]
  };
  let socialProfiles = [
    {
      name: "GitHub",
      url: "https://github.com/lucas-yotsui",
      src: "/images/github.svg",
    },
    {
      name: "LinkedIn",
      url: "https://www.linkedin.com/in/lucas-yukio-yotsui-de-carvalho-7b6492277",
      src: "/images/linkedin.svg",
    },
    {
      name: "Currículo",
      url: "https://drive.google.com",
      src: "/images/download.svg",
    }
  ]
</script>

<main>
  <div>
    <h1>Lucas Yukio</h1>
    <h2>Engenheiro Mecatrônico</h2>
  </div>

  <div>
    <p>Graduando pela Universidade Federal de Santa Catarina.</p>
    <p>Afiliado ao LISHA, anteriormente envolvido com o projeto OBNZIP e atualmente membro do IASE2.</p>
  </div>

  <div>
    <Chapters
      {chapters}
    >
    </Chapters>
  </div>

  <div>
    <Social
      {socialProfiles}
    >
    </Social>
  </div>
</main>

<style>
  main {
    display: flex;
    float: left;
    flex-direction: column;
    height: 100vh;
    width: 550px;
    padding: 0 30px 10px 30px;
    justify-content: space-between;
    box-sizing: border-box;
  }
  h1 {
    font-weight: 600;
    font-size: 80px;
    letter-spacing: -2px;
    margin: 0;
  }
  
  h2 {
    font-weight: 400;
    font-size: 35px;
    letter-spacing: -0.8px;
    margin: 0;
  }

  p {
    font-weight: 300;
    font-size: 20px;
    letter-spacing: -0.6px;
  }
</style>