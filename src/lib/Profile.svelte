<script>
	import Chapters from "./Chapters.svelte";

  let currentChapter = 1;
  let chapters = [
    {
      id: 1,
      name: "Projetos"
    },
    {
      id: 2,
      name: "Formação"
    }
  ];
</script>

<main>
  <h1>Lucas Yukio</h1>
  <h2>Engenheiro Mecatrônico</h2>

  <p>Graduando pela Universidade Federal de Santa Catarina.</p>
  <p>Afiliado ao LISHA, anteriormente envolvido com o projeto OBNZIP e atualmente membro do IASE2.</p>

  <Chapters
    currentChapter = {currentChapter}
    chapters = {chapters}
  >
  </Chapters>
</main>

<style>
  h1 {
    font-weight: 600;
    font-size: 80px;
    letter-spacing: -2px;
  }

  h2 {
    font-weight: 400;
    font-size: 35px;
    letter-spacing: -0.8px;
  }

  p {
    font-weight: 300;
    font-size: 20px;
    letter-spacing: -0.6px;
  }
</style>