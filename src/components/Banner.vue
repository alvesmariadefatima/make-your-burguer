<template>
  <div id="main-banner">
    <h1>Make Your Burger</h1>
  </div>
</template>

<script>
export default {
  name: "Banner"
}
</script>

<style scoped>
  #main-banner {
    background-image: url('/public/img/burger.jpg');
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    height: 50vh; /* Ajusta a altura para uma unidade relativa */
    display: flex;
    align-items: center;
    justify-content: center; /* Centraliza o conteúdo horizontalmente */
    padding: 0 20px; /* Adiciona padding para telas pequenas */
    box-sizing: border-box; /* Inclui padding na altura total do banner */
  }

  #main-banner h1 {
    color: #fff;
    text-align: center;
    font-size: 5vw; /* Usa viewport width para tornar o tamanho da fonte relativo ao tamanho da tela */
    background-color: rgba(34, 34, 34, 0.7); /* Adiciona transparência ao fundo */
    padding: 10px 20px; /* Ajusta o padding para telas menores */
    border-radius: 8px; /* Adiciona bordas arredondadas */
  }

  @media (max-width: 768px) {
    #main-banner {
      height: 40vh; /* Ajusta a altura para telas menores */
    }

    #main-banner h1 {
      font-size: 6vw; /* Ajusta o tamanho da fonte para telas menores */
      padding: 10px 15px; /* Ajusta o padding para telas menores */
    }
  }

  @media (max-width: 480px) {
    #main-banner {
      height: 30vh; /* Ajusta ainda mais a altura para telas muito pequenas */
    }

    #main-banner h1 {
      font-size: 8vw; /* Ajusta o tamanho da fonte para telas muito pequenas */
      padding: 8px 10px; /* Ajusta o padding para telas muito pequenas */
    }
  }
</style>