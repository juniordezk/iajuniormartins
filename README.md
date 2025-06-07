<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>IA Júnior Martins</title>
  <style>
    /* Estilos gerais */
    html, body {
      margin: 0;
      padding: 0;
      height: 100%; /* Garante que o fundo ocupe toda a tela */
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(to bottom right, #003300, #000000);
      color: #ffffff;
      text-align: center;
      padding: 50px 20px;
      height: 100%;
    }

    .logo {
      font-size: 36px;
      font-weight: bold;
      color: #00ffcc;
      margin-bottom: 40px;
      letter-spacing: 2px;
    }

    button {
      padding: 15px 40px;
      font-size: 22px;
      background-color: #00ffcc;
      color: #000;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    button:hover {
      background-color: #00ccaa;
    }

    /* Box de resultado */
    .sinal-box {
      margin-top: 50px;
      font-size: 28px;
      font-weight: bold;
      height: 100px;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.3s ease;
      color: white;
      white-space: pre-line;
    }

    /* Efeitos e animações */
    .buscando {
      color: #cccccc;
      animation: piscar 1s infinite;
    }

    @keyframes piscar {
      0% { opacity: 1; }
      50% { opacity: 0.3; }
      100% { opacity: 1; }
    }

    .azul {
      color: white;
      text-shadow: none;
      animation: none;
    }

    .vermelho {
      color: white;
      text-shadow: none;
      animation: none;
    }
/* Estilo do iframe para exibir o site de apostas */
    .apostas-container {
      margin-top: 50px; /* Dá espaço entre o sorteio e o site de apostas */
      width: 100%;
      height: 600px; /* Ajuste conforme necessário */
      border: none;
    }

    /* Estilo para esconder o conteúdo até a senha ser correta */
    #conteudo {
      display: none;
    }

    /* Estilo para bloquear interação até a senha ser correta */
    #bloqueado {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.7); /* Opacidade preta para bloquear */
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 24px;
      z-index: 9999;
    }

    /* Responsividade para dispositivos móveis */
    @media (max-width: 768px) {
      .logo {
        font-size: 28px; /* Ajusta o tamanho da logo */
      }

      button {
        font-size: 18px; /* Ajusta o tamanho do botão */
        padding: 12px 30px; /* Ajusta o padding do botão */
      }

      .sinal-box {
        font-size: 24px; /* Ajusta o tamanho da fonte do resultado */
      }

      .apostas-container {
        height: 400px; /* Ajusta o tamanho do iframe em dispositivos móveis */
      }
    }

    @media (max-width: 480px) {
      button {
        font-size: 16px; /* Ajusta o tamanho do botão para telas muito pequenas */
        padding: 10px 20px;
      }

      .sinal-box {
        font-size: 20px; /* Ajusta o tamanho da fonte do resultado para telas pequenas */
      }

      .apostas-container {
        height: 350px; /* Ajusta o tamanho do iframe para telas muito pequenas */
      }
    }
  </style>
</head>
<body>

  <div id="bloqueado">Acesso restrito. Por favor, digite a senha para continuar.</div>

  <div class="logo">IA Júnior Martins</div>
  <button onclick="buscarSinal()">BUSCAR SINAL</button>
  <div class="sinal-box" id="resultado"></div>

  <script>
    const senhaCorreta = "1234"; // Defina a senha aqui
    let isSenhaCorreta = false; // Variável para verificar se a senha foi corretamente inserida

    // Função para verificar a senha
    const verificarSenha = () => {
      let senha;

      // Enquanto a senha estiver incorreta, manter a solicitação de senha
      while (!isSenhaCorreta) {
        senha = prompt("Digite a senha para acessar o conteúdo:");

        if (senha === senhaCorreta) {
          isSenhaCorreta = true;
          document.getElementById("conteudo").style.display = "block"; // Exibe o conteúdo
          document.getElementById("bloqueado").style.display = "none"; // Remove o bloqueio
        } else {
          alert("Senha incorreta. Acesso negado.");
        }
      }
    };

    // Executa a função ao carregar a página
    window.onload = verificarSenha;

    function buscarSinal() {
      const resultadoDiv = document.getElementById('resultado');
      resultadoDiv.textContent = "Buscando entrada...";
      resultadoDiv.classList.add('buscando');
      resultadoDiv.classList.remove('azul', 'vermelho');

      setTimeout(() => {
        const sorteio = Math.random() < 0.5 ? 'azul' : 'vermelho';

        if (sorteio === 'azul') {
          resultadoDiv.textContent = "🔵PLAYER - PROBABILIDADE SEM GALE🎯";
          resultadoDiv.classList.add('azul'); // Nenhuma animação aplicada
        } else {
          resultadoDiv.textContent = "🔴BANKER - PROBABILIDADE SEM GALE🎯";
          resultadoDiv.classList.add('vermelho'); // Nenhuma animação aplicada
        }
      }, 2000); // Tempo de "buscando entrada"
    }
  </script>

  <!-- Conteúdo protegido -->
  <div id="conteudo">
    <iframe class="apostas-container" src="https://m.reals.bet.br/live-casino" title="Casa de Apostas Real's Bet" allowfullscreen></iframe>
  </div>

</body>
</html>
