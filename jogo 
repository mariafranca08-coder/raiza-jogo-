```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Pokémon Quiz</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial, sans-serif;
}

body{
    min-height:100vh;
    background:linear-gradient(135deg,#ffcb05,#3b4cca);
    display:flex;
    justify-content:center;
    align-items:center;
    padding:20px;
}

.game{
    width:100%;
    max-width:650px;
    background:white;
    border-radius:25px;
    padding:25px;
    text-align:center;
    box-shadow:0 10px 30px rgba(0,0,0,0.3);
}

.logo{
    font-size:60px;
}

h1{
    color:#3b4cca;
    margin:10px 0;
    font-size:36px;
}

.subtitulo{
    color:#666;
    margin-bottom:15px;
}

#numero{
    font-weight:bold;
    color:#555;
    margin-bottom:10px;
}

.imagem-pokemon{
    width:220px;
    height:220px;
    object-fit:contain;
    display:block;
    margin:0 auto 15px;
}

#pergunta{
    font-size:22px;
    font-weight:bold;
    color:#222;
    margin:15px 0 20px;
}

.opcoes{
    display:flex;
    flex-direction:column;
    gap:12px;
}

.opcao{
    width:100%;
    padding:17px;
    border:none;
    border-radius:15px;
    background:#3b4cca;
    color:white;
    font-size:18px;
    font-weight:bold;
    cursor:pointer;
}

.opcao:hover{
    background:#28358f;
}

.opcao:disabled{
    opacity:0.7;
    cursor:not-allowed;
}

#resultado{
    min-height:30px;
    margin-top:18px;
    font-size:19px;
    font-weight:bold;
}

#proximo,
#reiniciar{
    display:none;
    margin-top:15px;
    padding:14px 25px;
    border:none;
    border-radius:12px;
    background:#ffcb05;
    color:#222;
    font-size:17px;
    font-weight:bold;
    cursor:pointer;
}

#pontuacao{
    margin-top:18px;
    font-size:18px;
    font-weight:bold;
    color:#3b4cca;
}

#final{
    display:none;
}

#final h2{
    color:#3b4cca;
    font-size:32px;
    margin:15px;
}

#mensagemFinal{
    font-size:20px;
    line-height:1.5;
}

@media(max-width:500px){
    .imagem-pokemon{
        width:180px;
        height:180px;
    }

    h1{
        font-size:30px;
    }

    #pergunta{
        font-size:19px;
    }
}
</style>
</head>

<body>

<div class="game">

    <div id="jogo">

        <div class="logo">⚡🔴⚪</div>

        <h1>Pokémon Quiz!</h1>

        <p class="subtitulo">
            Escolha a resposta correta!
        </p>

        <p id="numero"></p>

        <img
            id="imagemPokemon"
            class="imagem-pokemon"
            alt="Imagem do Pokémon"
        >

        <div id="pergunta"></div>

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


    <div id="final">

        <div class="logo">🏆</div>

        <h2>Fim do jogo!</h2>

        <p id="mensagemFinal"></p>

        <button id="reiniciar" onclick="reiniciarJogo()">
            🔄 Jogar novamente
        </button>

    </div>

</div>


<script>

/* PERGUNTAS DO JOGO */

const perguntas = [

{
pergunta:"Quem é esse Pokémon elétrico amarelo?",
opcoes:["Pikachu","Squirtle"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/pikachu.jpg"
},

{
pergunta:"Qual Pokémon é do tipo água?",
opcoes:["Charmander","Squirtle"],
correta:1,
imagem:"https://img.pokemondb.net/artwork/large/squirtle.jpg"
},

{
pergunta:"Qual Pokémon usa ataques de fogo?",
opcoes:["Charmander","Bulbasaur"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/charmander.jpg"
},

{
pergunta:"Qual Pokémon é do tipo planta?",
opcoes:["Bulbasaur","Psyduck"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/bulbasaur.jpg"
},

{
pergunta:"Qual Pokémon é conhecido por dormir muito?",
opcoes:["Snorlax","Pikachu"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/snorlax.jpg"
},

{
pergunta:"Qual Pokémon é do tipo fantasma?",
opcoes:["Gengar","Ponyta"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/gengar.jpg"
},

{
pergunta:"Qual Pokémon pode evoluir para Vaporeon?",
opcoes:["Eevee","Mewtwo"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/eevee.jpg"
},

{
pergunta:"Qual destes é um Pokémon lendário?",
opcoes:["Mewtwo","Pidgey"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/mewtwo.jpg"
},

{
pergunta:"Qual Pokémon é uma raposa?",
opcoes:["Vulpix","Lapras"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/vulpix.jpg"
},

{
pergunta:"Qual Pokémon é conhecido por cantar?",
opcoes:["Jigglypuff","Machop"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/jigglypuff.jpg"
},

{
pergunta:"Qual Pokémon tem uma grande concha nas costas?",
opcoes:["Blastoise","Caterpie"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/blastoise.jpg"
},

{
pergunta:"Qual Pokémon evolui de Magikarp?",
opcoes:["Gyarados","Pikachu"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/gyarados.jpg"
},

{
pergunta:"Qual Pokémon é conhecido como Pokémon pato?",
opcoes:["Psyduck","Geodude"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/psyduck.jpg"
},

{
pergunta:"Qual Pokémon é do tipo dragão?",
opcoes:["Dragonite","Meowth"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/dragonite.jpg"
},

{
pergunta:"Qual Pokémon é conhecido por usar ataques de pedra?",
opcoes:["Geodude","Pikachu"],
correta:0,
imagem:"https://img.pokemondb.net/artwork/large/geodude.jpg"
}

];


let perguntaAtual = 0;
let pontuacao = 0;
let respondeu = false;


/* MOSTRAR A PERGUNTA */

function mostrarPergunta(){

    respondeu = false;

    const pergunta = perguntas[perguntaAtual];

    document.getElementById("numero").textContent =
    "Pergunta " + (perguntaAtual + 1) +
    " de " + perguntas.length;

    document.getElementById("pergunta").textContent =
    pergunta.pergunta;

    document.getElementById("opcao1").textContent =
    pergunta.opcoes[0];

    document.getElementById("opcao2").textContent =
    pergunta.opcoes[1];

    document.getElementById("imagemPokemon").src =
    pergunta.imagem;

    document.getElementById("resultado").textContent = "";

    document.getElementById("proximo").style.display = "none";

    document.getElementById("opcao1").disabled = false;
    document.getElementById("opcao2").disabled = false;
}


/* RESPONDER */

function responder(escolha){

    if(respondeu) return;

    respondeu = true;

    const pergunta = perguntas[perguntaAtual];

    const botao1 = document.getElementById("opcao1");
    const botao2 = document.getElementById("opcao2");

    if(escolha === pergunta.correta){

        pontuacao++;

        document.getElementById("resultado").textContent =
        "✅ Você acertou!";

    }else{

        document.getElementById("resultado").textContent =
        "❌ Você errou! A resposta era " +
        pergunta.opcoes[pergunta.correta];

    }

    document.getElementById("pontuacao").textContent =
    "⭐ Pontuação: " + pontuacao;

    botao1.disabled = true;
    botao2.disabled = true;

    document.getElementById("proximo").style.display =
    "inline-block";
}


/* PRÓXIMA PERGUNTA */

function proximaPergunta(){

    perguntaAtual++;

    if(perguntaAtual < perguntas.length){

        mostrarPergunta();

    }else{

        document.getElementById("jogo").style.display = "none";

        document.getElementById("final").style.display = "block";

        let mensagem;

        if(pontuacao >= 13){

            mensagem = "🌟 Incrível! Você é um Mestre Pokémon!";

        }else if(pontuacao >= 8){

            mensagem = "👏 Muito bem
! Você conhece bastante Pokémon!";

        }else{

            mensagem = "💪 Continue treinando para ficar ainda melhor!";

        }

        document.getElementById("mensagemFinal").innerHTML =
        mensagem +
        "<br><br>Você acertou <b>" +
        pontuacao +
        "</b> de <b>" +
        perguntas.length +
        "</b> perguntas!";

        document.getElementById("reiniciar").style.display =
        "inline-block";
    }
}


/* REINICIAR */

function reiniciarJogo(){

    perguntaAtual = 0;
    pontuacao = 0;
    respondeu = false;

    document.getElementById("jogo").style.display = "block";

    document.getElementById("final").style.display = "none";

    document.getElementById("pontuacao").textContent =
    "⭐ Pontuação: 0";

    mostrarPergunta();
}


/* INICIAR O JOGO */

mostrarPergunta();

</script>

</body>
</html>
```
