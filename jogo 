```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Pokémon - Quiz</title>

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
    max-width: 650px;
    background: white;
    border-radius: 30px;
    padding: 25px;
    text-align: center;
    box-shadow: 0 15px 40px rgba(0,0,0,0.35);
}

.logo {
    font-size: 55px;
}

h1 {
    color: #3b4cca;
    font-size: 38px;
    margin-bottom: 5px;
}

.subtitulo {
    color: #777;
    margin-bottom: 15px;
}

#numero {
    font-weight: bold;
    color: #555;
    margin-bottom: 12px;
}

.imagem-pokemon {
    width: 230px;
    height: 230px;
    object-fit: contain;
    margin: 5px auto 10px;
    display: block;
    background: #f2f2f2;
    border-radius: 25px;
    padding: 10px;
}

#pergunta {
    font-size: 23px;
    font-weight: bold;
    color: #222;
    margin: 15px 0 22px;
}

.opcoes {
    display: flex;
    flex-direction: column;
    gap: 14px;
}

.opcao {
    width: 100%;
    border: none;
    padding: 17px;
    border-radius: 15px;
    font-size: 18px;
    font-weight: bold;
    cursor: pointer;
    background: #3b4cca;
    color: white;
    transition: 0.2s;
}

.opcao:hover {
    background: #28358f;
    transform: scale(1.02);
}

.opcao:disabled {
    cursor: not-allowed;
    opacity: 0.8;
}

#resultado {
    min-height: 30px;
    margin-top: 18px;
    font-size: 20px;
    font-weight: bold;
}

#proximo {
    display: none;
    margin-top: 15px;
    padding: 14px 28px;
    border: none;
    border-radius: 14px;
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
    font-size: 32px;
    margin: 15px 0;
}

#mensagemFinal {
    font-size: 21px;
    margin: 15px;
}

#reiniciar {
    margin-top: 15px;
    padding: 15px 28px;
    border: none;
    border-radius: 14px;
    background: #3b4cca;
    color: white;
    font-size: 17px;
    font-weight: bold;
    cursor: pointer;
}

.estrela {
    font-size: 60px;
}

@media (max-width: 500px) {
    h1 {
        font-size: 30px;
    }

    .imagem-pokemon {
        width: 190px;
        height: 190px;
    }

    #pergunta {
        font-size: 20px;
    }
}
</style>
</head>

<body>

<div class="game">

    <!-- JOGO -->
    <div id="jogo">

        <div class="logo">🔴⚪</div>

        <h1>Pokémon Quiz!</h1>

        <p class="subtitulo">
            Teste seus conhecimentos Pokémon!
        </p>

        <p id="numero">Pergunta 1 de 15</p>

        <!-- IMAGEM DA PERGUNTA -->
        <img
            id="imagemPokemon"
            class="imagem-pokemon"
            src=""
            alt="Pokémon da pergunta"
        >

        <div id="pergunta"></div>

        <!-- DUAS OPÇÕES -->
        <div class="opcoes">

            <button
                class="opcao"
                id="opcao1"
                onclick="responder(0)">
            </button>

            <button
                class="opcao"
                id="opcao2"
                onclick="responder(1)">
            </button>

        </div>

        <div id="resultado"></div>

        <button id="proximo" onclick="proximaPergunta()">
            Próxima pergunta ➡️
        </button>

        <div id="pontuacao">
            ⭐ Pontuação: 0
        </div>

    </div>


    <!-- TELA FINAL -->
    <div id="final">

        <div class="estrela">🏆</div>

        <h2>Parabéns, treinador!</h2>

        <p id="mensagemFinal"></p>

        <button id="reiniciar" onclick="reiniciarJogo()">
            🔄 Jogar novamente
        </button>

    </div>

</div>


<script>

// =====================================================
// PERGUNTAS
// =====================================================

const perguntas = [

    {
        pergunta: "Qual Pokémon é conhecido por ser do tipo elétrico?",
        opcoes: ["Pikachu", "Squirtle"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/25.png"
    },

    {
        pergunta: "Qual destes Pokémon é do tipo água?",
        opcoes: ["Charmander", "Squirtle"],
        correta: 1,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/7.png"
    },

    {
        pergunta: "Qual Pokémon é conhecido por usar ataques de fogo?",
        opcoes: ["Charmander", "Bulbasaur"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/4.png"
    },

    {
        pergunta: "Qual Pokémon é do tipo planta?",
        opcoes: ["Bulbasaur", "Psyduck"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/1.png"
    },

    {
        pergunta: "Qual Pokémon evolui de Pichu?",
        opcoes: ["Pikachu", "Eevee"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/172.png"
    },

    {
        pergunta: "Qual Pokémon pode evoluir para Vaporeon?",
        opcoes: ["Eevee", "Mewtwo"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/133.png"
    },

    {
        pergunta: "Qual destes Pokémon é conhecido como um Pokémon lendário?",
        opcoes: ["Mewtwo", "Pidgey"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/150.png"
    },

    {
        pergunta: "Qual Pokémon é famoso por dormir bastante?",
        opcoes: ["Snorlax", "Pikachu"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/143.png"
    },

    {
        pergunta: "Qual destes Pokémon é do tipo fantasma?",
        opcoes: ["Gengar", "Ponyta"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/94.png"
    },

    {
        pergunta: "Qual Pokémon é conhecido por ser uma raposa?",
        opcoes: ["Vulpix", "Lapras"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/37.png"
    },

    {
        pergunta: "Qual destes Pokémon é do tipo água e psíquico?",
        opcoes: ["Psyduck", "Geodude"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/54.png"
    },

    {
        pergunta: "Qual Pokémon tem uma grande concha nas costas?",
        opcoes: ["Blastoise", "Caterpie"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/9.png"
    },

    {
        pergunta: "Qual Pokémon é conhecido como o Pokémon rato?",
        opcoes: ["Rattata", "Lapras"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/19.png"
    },

    {
        pergunta: "Qual Pokémon é uma evolução de Magikarp?",
        opcoes: ["Gyarados", "Jigglypuff"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/129.png"
    },

    {
        pergunta: "Qual Pokémon é conhecido por cantar e fazer os outros dormirem?",
        opcoes: ["Jigglypuff", "Machop"],
        correta: 0,
        imagem: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/39.png"
    }

];


// =====================================================
// VARIÁVEIS
// =====================================================

let perguntaAtual = 0;
let pontuacao = 0;
let respondeu = false;


// =====================================================
// MOSTRAR PERGUNTA
// =====================================================

function mostrarPergunta() {

    respondeu = false;

    const pergunta = perguntas[perguntaAtual];

    document.getElementById("numero").textContent =
        "Pergunta " +
        (perguntaAtual + 1) +
        " de " +
        perguntas.length;

    document.getElementById("pergunta").textContent =
        pergunta.pergunta;

    document.getElementById("opcao1").textContent =
        pergunta.opcoes[0];

    document.getElementById("opcao2").textContent =
        pergunta.opcoes[1];

    document.getElementById("imagemPokemon").src =
        pergunta.imagem;

    document.getElementById("resultado").textContent = "";

    document.getElementById("proximo").style.display =
        "none";

    document.getElementById("opcao1").disabled = false;
    document.getElementById("opcao2").disabled = false;
}


// =====================================================
// RESPONDER
// =====================================================

function responder(opcaoEscolhida) {

    if (respondeu) return;

    respondeu = true;

    const pergunta = perguntas[perguntaAtual];

    if (opcaoEscolhida === pergunta.correta) {

        pontuacao++;

        document.getElementById("resultado").textContent =
            "✅ ACERTOU! Muito bem, treinador!";

    } else {

        document.getElementById("resultado").textContent =
            "❌ ERROU! A resposta correta era: " +
            pergunta.opcoes[pergunta.correta];

    }

    document.getElementById("pontuacao").textContent =
        "⭐ Pontuação: " + pontuacao;

    document.getElementById("opcao1").disabled = true;
    document.getElementById("opcao2").disabled = true;

    document.getElementById("proximo").style.display =
        "inline-block";
}


// =====================================================
// PRÓXIMA PERGUNTA
// =====================================================

function proximaPergunta() {

    perguntaAtual++;

    if (perguntaAtual < perguntas.length) {

        mostrarPergunta();

    } else {

        document.getElementById("jogo").style.display =
            "none";

        document.getElementById("final").style.display =
            "block";

        let mensagem = "";

        if (pontuacao === 15) {
            mensagem =
                "🌟 PERFEITO! Você é um verdadeiro Mestre Pokémon!";
        }

        else if (pontuacao >= 11) {
            mensagem =
                "🔥 Muito bom! Você conhece muitos Pokémon!";
        }

        else if (pontuacao >= 7) {
            mensagem =
                "👍 Bom trabalho! Continue treinando!";
        }

        else {
            mensagem =
                "💪 Continue treinando e tente novamente!";
        }

        document.getElementById("mensagemFinal").innerHTML =
            mensagem +
            "<br><br>" +
            "Você acertou <strong>" +
            pontuacao +
            "</strong> de <strong>" +
            perguntas.length +
            "</strong> perguntas!";
    }
}


// =====================================================
// REINICIAR
// =====================================================

function reiniciarJogo() {

    perguntaAtual = 0;
    pontuacao = 0;

    document.getElementById("jogo").style.display =
        "block";

    document.getElementById("final").style.display =
        "none";

    document.getElementById("pontuacao").textContent =
        "⭐ Pontuação: 0";

    mostrarPergunta();
}



// =====================================================
// INICIAR
// =====================================================

mostrarPergunta();

</script>

</body>
</html>
```

