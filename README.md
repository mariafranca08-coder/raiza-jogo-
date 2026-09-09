```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Pokémon - Escolha Certa!</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    min-height: 100vh;
    background: linear-gradient(135deg, #ffcb05, #3b4cca);
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
}

.game {
    width: 100%;
    max-width: 600px;
    background: white;
    border-radius: 25px;
    padding: 30px;
    text-align: center;
    box-shadow: 0 10px 30px rgba(0,0,0,0.3);
}

h1 {
    color: #3b4cca;
    font-size: 38px;
    margin-bottom: 10px;
}

.pokebola {
    font-size: 70px;
    margin-bottom: 10px;
}

#numero {
    color: #777;
    margin-bottom: 20px;
}

#pergunta {
    font-size: 24px;
    color: #222;
    margin-bottom: 25px;
    min-height: 60px;
}

.opcoes {
    display: flex;
    flex-direction: column;
    gap: 15px;
}

.opcao {
    border: none;
    padding: 18px;
    border-radius: 15px;
    font-size: 18px;
    font-weight: bold;
    cursor: pointer;
    background: #3b4cca;
    color: white;
    transition: 0.2s;
}

.opcao:hover {
    transform: scale(1.03);
    background: #2d3aa5;
}

#resultado {
    margin-top: 20px;
    font-size: 20px;
    font-weight: bold;
    min-height: 30px;
}

#proximo {
    display: none;
    margin-top: 20px;
    padding: 14px 25px;
    border: none;
    border-radius: 12px;
    background: #ffcb05;
    color: #222;
    font-size: 17px;
    font-weight: bold;
    cursor: pointer;
}

#pontuacao {
    margin-top: 20px;
    font-size: 18px;
    font-weight: bold;
    color: #3b4cca;
}

#final {
    display: none;
}

#final h2 {
    color: #3b4cca;
    font-size: 30px;
    margin-bottom: 15px;
}

#reiniciar {
    margin-top: 20px;
    padding: 15px 25px;
    border: none;
    border-radius: 12px;
    background: #3b4cca;
    color: white;
    font-size: 17px;
    font-weight: bold;
    cursor: pointer;
}
</style>
</head>

<body>

<div class="game">

    <div id="jogo">

        <div class="pokebola">🔴⚪</div>

        <h1>Pokémon!</h1>

        <p id="numero">Pergunta 1</p>

        <div id="pergunta"></div>

        <div class="opcoes">
            <button class="opcao" onclick="responder(0)" id="opcao1"></button>
            <button class="opcao" onclick="responder(1)" id="opcao2"></button>
        </div>

        <div id="resultado"></div>

        <button id="proximo" onclick="proximaPergunta()">
            Próxima pergunta ➡️
        </button>

        <div id="pontuacao">
            Pontuação: 0
        </div>

    </div>

    <div id="final">

        <div class="pokebola">🏆</div>

        <h2>Fim do jogo!</h2>

        <p id="mensagemFinal"></p>

        <button id="reiniciar" onclick="reiniciarJogo()">
            Jogar novamente 🔄
        </button>

    </div>

</div>

<script>

const perguntas = [

    {
        pergunta: "Qual Pokémon é conhecido como o Pokémon elétrico?",
        opcoes: ["Pikachu", "Squirtle"],
        correta: 0
    },

    {
        pergunta: "Qual destes Pokémon é do tipo água?",
        opcoes: ["Charmander", "Squirtle"],
        correta: 1
    },

    {
        pergunta: "Qual Pokémon é conhecido por cuspir fogo?",
        opcoes: ["Charmander", "Bulbasaur"],
        correta: 0
    },

    {
        pergunta: "Qual destes Pokémon é do tipo planta?",
        opcoes: ["Bulbasaur", "Psyduck"],
        correta: 0
    },

    {
        pergunta: "Qual Pokémon evolui de Pichu?",
        opcoes: ["Pikachu", "Eevee"],
        correta: 0
    },

    {
        pergunta: "Qual destes Pokémon pode evoluir para Vaporeon?",
        opcoes: ["Eevee", "Mewtwo"],
        correta: 0
    }

];

let perguntaAtual = 0;
let pontuacao = 0;
let respondeu = false;

function mostrarPergunta() {

    respondeu = false;

    const pergunta = perguntas[perguntaAtual];

    document.getElementById("numero").textContent =
        "Pergunta " + (perguntaAtual + 1) + " de " + perguntas.length;

    document.getElementById("pergunta").textContent =
        pergunta.pergunta;

    document.getElementById("opcao1").textContent =
        pergunta.opcoes[0];

    document.getElementById("opcao2").textContent =
        pergunta.opcoes[1];

    document.getElementById("resultado").textContent = "";

    document.getElementById("proximo").style.display = "none";

    document.getElementById("opcao1").disabled = false;
    document.getElementById("opcao2").disabled = false;
}

function responder(opcaoEscolhida) {

    if (respondeu) return;

    respondeu = true;

    const pergunta = perguntas[perguntaAtual];

    if (opcaoEscolhida === pergunta.correta) {

        pontuacao++;

        document.getElementById("resultado").textContent =
            "✅ Acertou! Muito bem, treinador!";

    } else {

        document.getElementById("resultado").textContent =
            "❌ Errou! Tente acertar a próxima!";

    }

    document.getElementById("pontuacao").textContent =
        "Pontuação: " + pontuacao;

    document.getElementById("opcao1").disabled = true;
    document.getElementById("opcao2").disabled = true;

    document.getElementById("proximo").style.display = "inline-block";
}

function proximaPergunta() {

    perguntaAtual++;

    if (perguntaAtual < perguntas.length) {

        mostrarPergunta();

    } else {

        document.getElementById("jogo").style.display = "none";
        document.getElementById("final").style.display = "block";

        document.getElementById("mensagemFinal").textContent =
            "Você fez " + pontuacao + " de " +
            perguntas.length + " pontos!";

    }
}

function reiniciarJogo() {

    perguntaAtual = 0;
    pontuacao = 0;

    document.getElementById("jogo").style.display = "block";
    document.getElementById("final").style.display = "none";

    document.getElementById("pontuacao").textContent =
        "Pontuação: 0";

    mostrarPergunta();
}

mostrarPergunta();

</script>

</body>
</html>
```
