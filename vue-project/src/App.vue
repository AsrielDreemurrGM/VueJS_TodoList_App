<script setup>
import { reactive } from 'vue';

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

// Utilizando Eventos Para Manipular o DOM;
// Para conseguirmos alterar um valor no HTML no Vue isto não funciona:
// let contador = 0;
// Precisamos Criar um Estado da Aplicação;
const estados = reactive({
  contador: 0,
  email: '',
  saldo: 5000,
  transferindo: 0,
})

function aumentarContador() {
  estados.contador++;
}

function diminuirContador() {
  estados.contador--;
}

function alteraEmail(evento) {
  estados.email = evento.target.value;
}

// Estilização Condicional;

function mostraSaldoFuturo() {
// Utilizamos Desestruturação para Coletar os Valores;
  const {saldo, transferindo} = estados;
  return saldo - transferindo;
}

function temSaldoSuficiente() {
  const {saldo, transferindo} = estados;
  return saldo >= transferindo;
}
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
<h1>Acessando Váriaveis</h1>
<h3>{{ nome }}</h3>
<!-- Realizando um Cálculo Direto -->
<h3>{{ 10 + 10 }}</h3>
<!-- Acessando Propriedade de um Objeto -->
<h3>{{ meuObj.nome }}</h3>
<!-- Acessando Uma Função -->
<h3>{{ dizOla() }}</h3>
<!-- Adicionando Uma Imagem Via Link Em Uma Variável -->
<!-- Separando Conteúdo -->
<br><hr>
<h1>Acessando Imagem</h1>
<!-- Não Utilizamos as Chaves "{}", Utilizamos "v-bind:nomeDoAtributo"="variavel" -->
<!-- Podemos também utilizar um atalho para este comando, ficando assim: ":nomeDoAtributo"="variavel"-->
<img :src="enderecoDaImagemUndertale" alt="">

<!-- Separando Conteúdo -->
<br><hr>

<h1>Acessando Botão</h1>
<!-- Podemos utilizar o v-bind também em botões: -->
<button :disabled="botaoEstaDesabilitado">Enviar Mensagem</button>

<!-- Separando Conteúdo -->
<br><hr>

<!-- Renderização Condicional -->
<h1>Renderizando Imagens Com Renderição Condicional</h1>
<!-- O Valor está definido como "false", então a imagem não aparece -->
<img v-if="conheceUndertale" :src="enderecoDaImagemUndertale" alt="">
<!-- Utilizando o "v-else-if" para Alternar Entre duas Imagens -->
<img v-else-if="conheceMinecraft" :src="enderecoDaImagemMinecraft" alt="">
<!-- Utilizando o "v-else" para se Caso Nenhuma das Imagens tiver Valor "true" -->
<h2 v-else="">Não conhece nenhum dos jogos - Ambos valores Como "false", Nenhuma Imagem a Mostrar</h2>
<!-- Podemos utilizar o "v-show" também para mostrar a imagem -->
<!-- Porém o "v-show" com o Valor "false" Carrega a Imagem, somente Não Mostra ela -->
<!-- Enquanto o "v-if" Não Irá Nem Carrega a Imagem no HTML -->
<img v-show="conheceUndertale" :src="enderecoDaImagemUndertale" alt="">

<!-- Separando Conteúdo -->
<br><hr>

<!-- Outro exemplo do "v-if" -->
<h1>Verificando Acesso</h1>
<!-- Valor se for "true" -->
<h3 v-if="estaAutorizado">Seja Bem-Vindo!</h3>
<!-- Valor se for "false" -->
<h3 v-else>Não Possui Acesso.</h3>

<!-- Separando Conteúdo -->
<br><hr>

<!-- Utilizando Eventos Para Manipular o DOM -->
<h3>Contador</h3>
{{ estados.contador }}

<!-- Acessamos Eventos com o "@" -->
<button @click="aumentarContador" type="button">+</button>
<button @click="diminuirContador" type="button">-</button>

<!-- Separando Conteúdo -->
<br><hr>

<!-- Recuperando um Valor de um Input -->
<h3>Digite um E-mail</h3>
{{ estados.email }}
<!-- Utilizamos o "@keyup", pois o "@change" só altera o valor do campo -->
<!-- quando clicamos fora dele -->
<!-- Aqui podemos utilizar uma Arrow Function -->
<!-- <input type="email" @keyup="evento => estados.email = evento.target.value"> -->
<!-- Para não utilizar uma Arrow Function podemos chamar uma função normal: -->
<input type="email" @keyup="alteraEmail()">

<!-- Separando Conteúdo -->
<br><hr>

<!-- Estilização Condicional -->
<h3>O Campo Deve Ficar Vermelho se o Valor do Saldo for Insuficiente</h3>
Saldo: {{ estados.saldo }} <br>
Transferindo: {{ estados.transferindo }} <br>
Saldo depois da transferência: {{ mostraSaldoFuturo() }} <br>
<!-- Para Fazer a Condição Utilizamos as Chaves Simples "{}" Não Duplas "{{ - }}" -->
<!-- Se a Função "temSaldoSuficiente" Não Retornar "true" Aplica Invalidez-->
<input :class="{ invalido: !temSaldoSuficiente() }" type="number" 
  placeholder="Quantidade a Transferir" 
  @keyup="evento => estados.transferindo = evento.target.value">
<br>
<button v-if="temSaldoSuficiente()">Transferir</button>
<span v-else>Valor Maior que o Saldo Disponível</span>
</template>

<style scoped>
img {
  max-width: 200px;
}

/* Estilização Condicional */
.invalido {
  outline-color: red;
  border-color: red;
}
</style>
