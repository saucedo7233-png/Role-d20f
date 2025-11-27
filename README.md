<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>D20 3D – Rolador de Dados</title>
<style>
    body {
        margin: 0;
        background: #0a0a0a;
        color: white;
        font-family: Arial, sans-serif;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding-top: 30px;
    }

    /* AREA DO DADO */
    #dice {
        width: 120px;
        height: 120px;
        background: red;
        border-radius: 10px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 40px;
        font-weight: bold;
        color: white;
        transition: transform 0.6s ease;
    }

    /* BOTÕES */
    .btns {
        margin-top: 20px;
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
        justify-content: center;
    }

    button {
        background: red;
        border: none;
        padding: 10px 18px;
        color: white;
        font-size: 18px;
        border-radius: 8px;
        cursor: pointer;
    }

    button:hover {
        background: #ff3030;
    }

    /* RESULTADOS BOLINHAS */
    .results {
        margin-top: 25px;
        display: flex;
        gap: 10px;
        flex-wrap: wrap;
        justify-content: center;
    }

    .ball {
        width: 40px;
        height: 40px;
        background: white;
        color: black;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 50%;
        font-weight: bold;
        font-size: 18px;
    }

    /* RESPONSIVIDADE */
    @media (max-width: 600px) {
        #dice {
            width: 100px;
            height: 100px;
            font-size: 35px;
        }
        button {
            font-size: 16px;
        }
        .ball {
            width: 35px;
            height: 35px;
            font-size: 16px;
        }
    }
</style>
</head>
<body>

<h1>D20 3D</h1>

<div id="dice">20</div>

<div class="btns">
    <button onclick="roll(1)">Rodar 1x</button>
    <button onclick="roll(2)">Rodar 2x</button>
    <button onclick="roll(3)">Rodar 3x</button>
    <button onclick="roll(4)">Rodar 4x</button>
    <button onclick="roll(5)">Rodar 5x</button>
</div>

<div class="results" id="results"></div>

<script>
function randomD20() {
    return Math.floor(Math.random() * 20) + 1;
}

function roll(times) {
    const dice = document.getElementById("dice");
    const resultsDiv = document.getElementById("results");

    resultsDiv.innerHTML = "";  // Limpa os resultados

    // ANIMAÇÃO DE GIRO
    dice.style.transform = "rotateX(" + (Math.random()*360) + "deg) rotateY(" + (Math.random()*360) + "deg)";

    setTimeout(() => {
        for (let i = 0; i < times; i++) {
            let result = randomD20();

            // Mostra o número grande no dado
            dice.textContent = result;

            // Cria bolinha
            const ball = document.createElement("div");
            ball.className = "ball";
            ball.textContent = result;
            resultsDiv.appendChild(ball);
        }
    }, 500);
}
</script>

</body>
</html>
