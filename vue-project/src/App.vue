<script setup>
const nome = "Eduardo";
const meuObj = {
  nome: "Eduardo Augusto",
  filmeFavorito: "Não Sei"
}

function dizOla() {
  return `${nome} Disse Olá!`;
}

const enderecoDaImagemUndertale = "https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi1nnJCJIHFQWJl4syczMn__Ym1P5eNGUEo_aI8_GhU2vjoCa0grWAm9tbryx8efgdbAGVvWxgtF_qXQfvimrf-OMFz5rY2YCtcE-FcvvnvyNc0DyjHchdHHhWbxN90GC-N6u4XUs0VRR5_/s1600/undertale.jpg";

const botaoEstaDesabilitado = true;

// Renderização Condicional
// Consiste em um código que só é executado somente caso alguma condição seja cumprida;
// Fazemos isto com Diretivas, que é um atributo do VueJS como o "v-bind";
// Diretivas são Criadas com "v-if";
const conheceUndertale = false;

const enderecoDaImagemMinecraft = "https://play-lh.googleusercontent.com/27O5tpaYE82W6m30rJ_MX3-UvshlDM6O8oXDxb6GseYW2T7P8UNT19727MGmz-0q3w";

const conheceMinecraft = false;

const estaAutorizado = true;
</script>

<template>
<!-- Para inserirmos um conteúdo no HTMl no JavaScript fazemos da seguinte maneira: -->
<!-- document.querySelector('h1').innerHTML = nome; -->
<!-- Porém, com Frameworks, precisamos utilizar as maneiras que os prórios Frameworks -->
<!-- nos fornecem, com o VueJS fazemos da seguinte maneira, utilizando as Chaves "{}": -->
<!-- <exemplo>{{ nomeDaVariavel }}</exemplo> -->
<!-- Com o VueJS os valores são acessados e processados como se fossem JavaScript -->
<!-- Então podemos acessa-los das seguintes maneiras: -->
<!-- Acessando uma Variável -->
<h1>{{ nome }}</h1>
<!-- Realizando um Cálculo Direto -->
<h1>{{ 10 + 10 }}</h1>
<!-- Acessando Propriedade de um Objeto -->
<h1>{{ meuObj.nome }}</h1>
<!-- Acessando Uma Função -->
<h1>{{ dizOla() }}</h1>
<!-- Adicionando Uma Imagem Via Link Em Uma Variável -->
<!-- Não Utilizamos as Chaves "{}", Utilizamos "v-bind:nomeDoAtributo"="variavel" -->
<!-- Podemos também utilizar um atalho para este comando, ficando assim: ":nomeDoAtributo"="variavel"-->
<img :src="enderecoDaImagemUndertale" alt="">
<!-- Podemos utilizar o v-bind também em botões: -->
<button :disabled="botaoEstaDesabilitado">Enviar Mensagem</button>

<!-- Renderização Condicional -->
<!-- O Valor está definido como "false", então a imagem não aparece -->
<img v-if="conheceUndertale" :src="enderecoDaImagemUndertale" alt="">
<!-- Utilizando o "v-else-if" para Alternar Entre duas Imagens -->
<img v-else-if="conheceMinecraft" :src="enderecoDaImagemMinecraft" alt="">
<!-- Utilizando o "v-else" para se Caso Nenhuma das Imagens tiver Valor "true" -->
<h2 v-else="">Não conhece nenhum dos jogos</h2>
<!-- Podemos utilizar o "v-show" também para mostrar a imagem -->
<!-- Porém o "v-show" com o Valor "false" Carrega a Imagem, somente Não Mostra ela -->
<!-- Enquanto o "v-if" Não Irá Nem Carrega a Imagem no HTML -->
<img v-show="conheceUndertale" :src="enderecoDaImagemUndertale" alt="">
<!-- Outro exemplo do "v-if" -->
<!-- Valor se for "true" -->
<h1 v-if="estaAutorizado">Seja Bem-Vindo!</h1>
<!-- Valor se for "false" -->
<h1 v-else>Não Possui Acesso.</h1>
</template>

<style scoped>
img {
  max-width: 200px;
}
</style>
