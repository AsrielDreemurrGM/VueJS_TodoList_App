<script setup>
const nome = "Eduardo";
const meuObj = {
  nome: "Eduardo Augusto",
  filmeFavorito: "Não Sei"
}

function dizOla() {
  return `${nome} Disse Olá!`;
}

const enderecoDaImagem = "https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi1nnJCJIHFQWJl4syczMn__Ym1P5eNGUEo_aI8_GhU2vjoCa0grWAm9tbryx8efgdbAGVvWxgtF_qXQfvimrf-OMFz5rY2YCtcE-FcvvnvyNc0DyjHchdHHhWbxN90GC-N6u4XUs0VRR5_/s1600/undertale.jpg";

const botaoEstaDesabilitado = true;
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
<img :src="enderecoDaImagem" alt="">
<!-- Podemos utilizar o v-bind também em botões: -->
<button :disabled="botaoEstaDesabilitado">Enviar Mensagem</button>
</template>

<style scoped>

</style>
