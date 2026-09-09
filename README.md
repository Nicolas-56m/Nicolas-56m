<div align="center">
<img src="https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=Bem%20Vindos!!!%20Sinta-se%20a%20%Vontade&fontSize=40&fontAlignY=40" />

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/16ddb49c-42fe-4ea4-97fc-1718139dfe48" />

# Olá, sou o Nicolas, bem vindo ao meu perfil! 
## Aqui falo sobre os meus conhecimentos 👇🏼

### 🎓 Estudante de Desenvolvimento de Sistemas

<img src="https://img.shields.io/badge/SENAI(DS)-%2B1200h-red">
<img src="https://img.shields.io/badge/ServiceNow-32H-brightgreen">
<img src="https://img.shields.io/badge/(DS)Banco%20de%20Dados-blue">
<img src="https://img.shields.io/badge/(DS)Sistemas%20Operacionais-orange">

</div>

<div align="center">

## <h2>📚 Formação</h2>

<img src="https://img.shields.io/badge/SENAI-%2B1200h-red">
<img src="https://img.shields.io/badge/ServiceNow-SENAI-brightgreen">

- Analista e Desenvolvedor de Sistemas (SENAI | +1200h)
- Plataforma ServiceNow University (SENAI | 32h)
  
## <h2>💻 Conhecimentos</h2>

<img src="https://img.shields.io/badge/(DS)Banco%20de%20Dados-blue">
<img src="https://img.shields.io/badge/(DS)Sistemas%20Operacionais-orange">

- Banco de Dados
- Sistemas Operacionais
- ServiceNow
- Códigos em Portugol, em C, HTML, CSS e JavaScript
  
</div>

## 🚀 Projetos

- 🐍 Cobra Auto
 
<img src="https://raw.githubusercontent.com/Nicolas-56m/Nicolas-56m/output/github-snake-dark.svg">
 
- 🏓 Pong Auto

  <!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ping Pong</title>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            background: #111;
            color: white;
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
        }

        h1 {
            margin-bottom: 10px;
        }

        #placar {
            font-size: 32px;
            margin-bottom: 15px;
        }

        canvas {
            background: black;
            border: 3px solid white;
            max-width: 95%;
        }

        p {
            margin-top: 15px;
            color: #ccc;
        }
    </style>
</head>

<body>

    <h1>🏓 Ping Pong</h1>

    <div id="placar">
        <span id="jogador">0</span>
        -
        <span id="computador">0</span>
    </div>

    <canvas id="jogo" width="800" height="500"></canvas>

    <p>Use as teclas ↑ e ↓ para controlar a raquete.</p>

    <script>
        const canvas = document.getElementById("jogo");
        const ctx = canvas.getContext("2d");

        const jogadorPlacar = document.getElementById("jogador");
        const computadorPlacar = document.getElementById("computador");

        let jogadorPontos = 0;
        let computadorPontos = 0;

        const raquete = {
            largura: 15,
            altura: 100,
            velocidade: 7
        };

        const jogador = {
            x: 20,
            y: canvas.height / 2 - 50,
            largura: raquete.largura,
            altura: raquete.altura
        };

        const computador = {
            x: canvas.width - 35,
            y: canvas.height / 2 - 50,
            largura: raquete.largura,
            altura: raquete.altura,
            velocidade: 5
        };

        const bola = {
            x: canvas.width / 2,
            y: canvas.height / 2,
            tamanho: 12,
            velocidadeX: 5,
            velocidadeY: 5
        };

        let cima = false;
        let baixo = false;

        document.addEventListener("keydown", function(event) {
            if (event.key === "ArrowUp") {
                cima = true;
            }

            if (event.key === "ArrowDown") {
                baixo = true;
            }
        });

        document.addEventListener("keyup", function(event) {
            if (event.key === "ArrowUp") {
                cima = false;
            }

            if (event.key === "ArrowDown") {
                baixo = false;
            }
        });

        function desenharRaquete(x, y, largura, altura) {
            ctx.fillStyle = "white";
            ctx.fillRect(x, y, largura, altura);
        }

        function desenharBola() {
            ctx.fillStyle = "white";
            ctx.fillRect(
                bola.x,
                bola.y,
                bola.tamanho,
                bola.tamanho
            );
        }

        function desenharLinha() {
            ctx.setLineDash([10, 10]);
            ctx.beginPath();

            ctx.moveTo(canvas.width / 2, 0);
            ctx.lineTo(canvas.width / 2, canvas.height);

            ctx.strokeStyle = "white";
            ctx.stroke();

            ctx.setLineDash([]);
        }

        function moverJogador() {
            if (cima && jogador.y > 0) {
                jogador.y -= raquete.velocidade;
            }

            if (baixo && jogador.y + jogador.altura < canvas.height) {
                jogador.y += raquete.velocidade;
            }
        }

        function moverComputador() {
            const centroComputador =
                computador.y + computador.altura / 2;

            if (centroComputador < bola.y) {
                computador.y += computador.velocidade;
            } else {
                computador.y -= computador.velocidade;
            }

            if (computador.y < 0) {
                computador.y = 0;
            }

            if (computador.y + computador.altura > canvas.height) {
                computador.y = canvas.height - computador.altura;
            }
        }

        function colisao(raquete) {
            return (
                bola.x < raquete.x + raquete.largura &&
                bola.x + bola.tamanho > raquete.x &&
                bola.y < raquete.y + raquete.altura &&
                bola.y + bola.tamanho > raquete.y
            );
        }

        function reiniciarBola() {
            bola.x = canvas.width / 2;
            bola.y = canvas.height / 2;

            bola.velocidadeX *= -1;

            bola.velocidadeY =
                Math.random() > 0.5 ? 5 : -5;
        }

        function atualizar() {
            moverJogador();
            moverComputador();

            bola.x += bola.velocidadeX;
            bola.y += bola.velocidadeY;

            if (bola.y <= 0 ||
                bola.y + bola.tamanho >= canvas.height) {

                bola.velocidadeY *= -1;
            }

            if (colisao(jogador) && bola.velocidadeX < 0) {
                bola.velocidadeX *= -1;
            }

            if (colisao(computador) && bola.velocidadeX > 0) {
                bola.velocidadeX *= -1;
            }

            if (bola.x < 0) {
                computadorPontos++;
                computadorPlacar.textContent = computadorPontos;

                reiniciarBola();
            }

            if (bola.x > canvas.width) {
                jogadorPontos++;
                jogadorPlacar.textContent = jogadorPontos;

                reiniciarBola();
            }
        }

        function desenhar() {
            ctx.clearRect(
                0,
                0,
                canvas.width,
                canvas.height
            );

            desenharLinha();

            desenharRaquete(
                jogador.x,
                jogador.y,
                jogador.largura,
                jogador.altura
            );

            desenharRaquete(
                computador.x,
                computador.y,
                computador.largura,
                computador.altura
            );

            desenharBola();
        }

        function jogo() {
            atualizar();
            desenhar();

            requestAnimationFrame(jogo);
        }

        jogo();
    </script>

</body>
</html>

- ☄️ Asteroids Auto
- Trabalho/Github
- Repositório de Códigos Feitos por mim (Códigos em Portugol e em C)

📫 Sempre em busca de novos conhecimentos na área de tecnologia.
