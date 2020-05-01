---
title: "Mais um guia de JavaScript"
date: 2020-04-30T21:39:07-03:00
tags : [ "dev", "javascript", "languages"]
categories : [ "dev" ]
layout: post
weight: 1
---

# JavaScript
- Informações compiladas por João G.J. Marinho a.k.a Pato do ICMC/USP
- A idéia foi compilar os conteúdos necessários de JavaScript puro antes de adentrar o mundo dos frameworks
# Índice

### Introdução

1) [Comentários do Autor](#comentários-do-autor)
2) [O que é JavaScript](#o-que-é-javascript)
3) [O que o JavaScript pode fazer](#o-que-o-javascript-pode-fazer)
4) [Bibliografia Essencial](#bibliografia-essencial)

### Iniciando no Javascript

5) [Conectando o JavaScript na sua pagina HTML](#conectando-o-javascript-na-sua-pagina-html)
6) [Estrutura e Tipos de Dados](#estrutura-e-tipos-de-dados)
7) [Comparações e suas Peculiaridades](#comparações-e-suas-peculiaridades)
8) [Controle de Fluxo](#controle-de-fluxo)

### Especificicações do Javascript

9)  [Funções](#funções)
10) [Eventos](#eventos)
11) [Objetos](#objetos)
12) [JSON](#json)
13) [Arrays](#arrays)
14) [Métodos para Arrays](#métodos-para-arrays)
15) [JavaScript Assíncrono](#javascript-assíncrono)
16) [Módulos (Exportando e Importando)](#módulos)
17) [Requests usando Axios](#requests-usando-axios)

Fico devendo um capítulo sobre manipulação do DOM

## Comentários do Autor
- Ao longo deste manual, será possível perceber que o JavaScript é uma linguagem muito dinâmica e que deixa você fazer muitas coisas que algumas outras linguagens mais estritas não permitiriam

- Há um motivo muito bom pra isso: o JavaScript tem um foco muito grande em ser compátivel com a maior quantidade possível de navegadores e sistemas
- Isso é uma faca de dois gumes, pois, ao mesmo tempo que há suporte para navegadores lançados a 15 anos atŕas, o JavaScript se obriga a manter funcionalidades antiquadas e que não obedecem as "atuais melhores práticas" de programação
- Portanto é importante se policiar quando busca informações sobre a linguagem, houveram muitas mudanças com a introdução do EcmaScript 6 em 2015. Se pesquisar no StackOverflow, **veja a data de postagem da dúvida, preste atenção no uso de "var" (método antigo) ao invés de "let" e "const", e ao uso de jQuery por exemplo**

## O que é JavaScript

- Surgiu como uma linguagem para o navegador, com o objetivo de "tornar a pagina mais viva"
- É uma linguagem de programação interpretada, portanto os scripts não precisam ser compilados préviamente
- Além disso, é uma linguagem extremamente flexível com sua **"tipagem dinâmica fraca"**
  - Isto significa que a linguagem não necessita de declarações de tipo de dados

Por Exemplo:
```javascript
let variavel1 = 30; // Veja que não necessitamos declarar se é um int ou string
let texto = "Olá, eu sou um texto"; // Mesmo caso para textos

let variavel1 = texto // A tipagem dinâmica permite transformar uma variável
                      // Que inicialmente era int em uma string
```

-  Tudo isso garante para o JavaScript uma velocidade muito rápida de implementação de código e prototipagem.
- O Javascript vem ganhando fatias do mercado de backend com tecnologias como **`node`** e serviços de infraestrutura que usam o javascript como linguagem principal como **``Amazon Web Services e Google Cloud Platform``**


## O que o JavaScript Pode Fazer?

- Esta questão é altamente dependente do ambiente em que você utiliza o Javascript
- No navegador o Javascript pode adicionar HTML, Reagir ao Usuário, Mandar requisições pela Internet, etc
- No computador o Node age como "middlemen" em relação ao JavaScript, permitindo que ele execute muito mais funções do que no navegador, inclusive leitura e escrita em arquivos do sistema.


## Bibliografia essencial

- [Mozilla Developer Network](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference)
- [Informações sobre compatibilidade de Funcionalidades do JavaScript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference)
- [JavaScript.info](https://javascript.info/)


---

---
## Conectando o JavaScript na Sua Pagina HTML
- Para adicionar JavaScript numa pagina HTML precisamos utilizar a tag "script
- A duas maneiras principais:
  - Adicionar o JavaScript dentro da própria pagina 
  - Adicionar um link ou diretório para um arquivo ".js"

```html
Maneira 1
<script>
  let variavel = "dentro do javascript";
  alert(variavel);
</script>

Maneira 2
<script src="diretorio/do/script.js"></script>
```

## Estrutura e Tipos de Dados

### Exemplos de Declaração
```javascript
// A seguir algumas declarações:
alert("Você foi hackeado");
console.log("Aparece no Console de Desenvolvedor");

// Na maioria das vezes não é necessário o ";"
alert("Funciona perfeitamente sem o ;")
alert("Mas ainda é uma boa ideia usá-lo");
// Em alguma linha de código muito exotérica 
// o JavaScript pode não ler corretamente suas declarações
```

### Tipos de Variáveis

- Para declarar uma variável usamos duas palavras-chaves:
  - let -> Variáveis mutáveis, com escopo.
  - const -> Variáveis imutáveis, também com escopo
```javascript
// Variáveis criadas com let possuem escopo da mesma maneira
// que você esta acostumado na maioria das linguagens
let variavel = "textinho legal"; 

// const define variáveis constantes, ou seja
// que não mudam. É util para definir funções também
const variavel_constante = 30; 

```
- Antigamente o único tipo de variável que o JavaScript possuia era "var"

```js
// Ela tem algumas peculiaridades e foi largamente
// Substituida por let e const
var variavel_antiga = 40; 
```



### Tipos de Dados

- Numérico
```javascript
// Numéricos são tratados de maneira igual, independente de serem float ou int
let numero = 30;
let flutuante = 23.2;
```

- Strings
```js
let comum = "String Comum";
let crase = `Crase ao invés de aspas possibilita a inserção de variáveis assim: ${comum}`
// Podemos inserir uma variável na string usando a notação ${var}
// Facilita quando você estiver fazendo uma string com muitas variáveis
```
- Booleano
  - Verdadeiro ou Falso
```js
let verdadeiro = true;
let falso = false;
```

#### Outros tipos

- Undefined - Indefinido
  - Declarado sem valor, ou função sem retorno retornam undefined por exemplo
```js
let x; // Não declarei valor
alert(x) // resultado: undefined
```

- Null - Nulo
```js
let nao_sei = null; // Não sei o valor ainda
                    // portanto defino como null para evitar erros
```

- Objetos e Arrays
  - Coleções de dados
  - Base do JSON
  - Vão ser explorados mais a fundo depois
```js
let objeto = {
  tipo: "Objetivo",
  nome: "Vespucio",
  legal: "Muito"
};

let array = [1, 2, 3, 4, 5];
```

- No JavaScript, funções são consideradas dados (e também objetos) e podem ser armazenadas em variáveis. Mas isso fica pra outra hora.

## Comparações e Suas Peculiaridades

- Em grande parte ele se assemelha as outras linguagens,  porém temos que tomar cuidado com algumas peculiaridades:
- Qual será o resultado para:
```javascript
let texto = "";
let numero = 0;

alert(texto == numero); // True!
```
- O JavaScript sempre tenta transformar um dado de qualquer tipo que seja em número, portanto quando realizamos essa comparação o texto vazio se torna um 0
- Para contornar isso temos o "===" que é uma igualdade estrita
  - Assim, se o JavaScript encontra tipos diferentes ele retorna false antes mesmo de comparar
```js
let texto = "";
let numero = 0;

alert(texto === numero); // False!!!
```
- Outra peculiaridade é que é possível comparar textos
- Comparação letra por letra na tabela ASCII

```js
alert("banana" > "maça") // False, Banana vem antes no dicionário
```

## Controle de Fluxo

- Durante a execução dos nossos scripts, muitas vezes nos deparamos com situações em que queremos realizar determinadas tarefas apenas quando uma variável é verdadeira ou quando o usuário clica em algum botão por exemplo
- Imagine isso como o fluxo de um sistema hidráulico, se abrirmos uma torneira, é porque queremos que a água passe naquela direção e vice-versa.
- Isto é chamado de Flow Control ou "Controle de Fluxo", e o JavaScript tem várias ferramentas para realizar este contorle

### if, else if & else
```javascript
let a = 100;
let b = 20;

// if / else if / else
if (a > b){
  alert(`O número ${a} é maior que o número ${b}`);
} else if (b > a) {
  alert(`O número ${b} é maior que o número ${a}`);
} else {
  alert(`O número ${b} é igual ao número ${a}`);
}
```

### Operador ternário "?"
- Definido por um ponto de interrogação: "?"
- Este operador é basicamente um if else reduzido, para compactar o código

```javascript
let b = 20;
let a = 30;
let maior = null;

// Podemos traduzir a seguinte expressão

if (a > b){
  maior = a;
} else {
  maior = b;
}

// Em uma linha:

// a > b ? SE SIM maior = a : SE NÃO maior = b
let maior = (a > b) ? a : b;
// No início pode parecer estranho mas é uma mão na roda
```

### Tipos de Loops:

```javascript
// while (enquanto a condição for verdadeira)
while(true){ // Sempre sera verdade
  console.log("AHHHHH LOOP INFINITO");
}

// Do while, executa uma vez depois checa se a condição é verdadeira
do{
  console.log( "Só executo uma vez :(" );
} while(false) // Não é pra repetir
// mas o código executa uma vez por conta do "do"


// for, que permite declarar uma variável 
// que só existe durante a execução do Loop
// normalmente essa variável é um contador.
// Por convenção se usa o "i", "j" e "k", nesta sequencia

// Declaração de Variavel ; Condição ; Expressão de Finalização
for (let i = 0; i < 10; i++){
  console.log(`QUACK ${i}`); // Sera impresso até que a variável i seja igual a 10
}
```
## Funções
### Tipos de Funções e suas Declarações
- No JavaScript, funções são tratados como valores comuns, e podem até ser inseridas dentro de uma variável
- Portanto, temos três maneiras de declarar funções no JavaScript:
```js
// A primeira e mais simples é declarando uma função
// usando a palavra-chave "function"

// Método 1 - Declaração de Função ou Function Declaration
function imprimirNaTela(texto) {
  console.log(texto);
}
// Provavelmente você ja viu isso em outras linguagens


// A diferença vem nos próximos dois métodos:

// Método 2 - Expressão de Função ou Function Expression
let imprimirNaTela = function(texto){ 
  console.log(texto);
}; // Perceba o ; no fim da variável


// Método 3 -  Função "Flecha" ou Arrow Function
let imprimirNaTela = (texto) => console.log(texto);
```
### Diferenças entre os tipos de funções
- A Declaração de Função (1) cria a função no início da interpretação do Script, portanto podemos usá-la antes da linha em que a declaramos de fato (Exemplo: declarar funções no fim do seu código, mas requisitá-las no início da função)
- Ja no método (2) e (3), Só podemos usar a função depois da linha em que ela foi declarada.
- Além disso, o método (2) e (3) podem ser visualizados fora do escopo inicial da função, desde que a variável que carrega a função seja declarada no escopo em que pretendemos utilizá-la
- O método (3) é muito útil para funções curtas, visto que pode ser usado em apenas uma linha

## Eventos
### O que são Eventos
- Um Evento é um sinal de que algo aconteceu
- Todos as partes de uma página tem capacidade de gerar esses sinais
- Exemplos de sinais que podem ser registrados através de eventos
  - Movimento do Mouse
  - Pressionar do teclado
  - Clique de um botão
  - Animações de CSS
  - Entre outras

### Como criar Eventos
- Lidamos com esses eventos através de "Event Handlers"
- Event Handlers podem ser feitos no próprio HTML
```html
<script>
  let count = 0;
  function contador() {
    count++
    alert(count);
  }
</script>

<!-- Perceba o "onclick" -> Ele é um tipo de Event Handler
     Podemos usar vários eventos usando a notação onEVENTO="funcao()"--> 
<button onclick="contador()"></button>
```
- Ou através de "Event Listeners" no Javascript através do método addEventListener

```js
// addEventListener() é um método para elementos HTML que recebe
// dois parâmetros principais: (Evento a ser "ouvido", Função a ser executada)

// Perceba o uso da Arrow Function como segundo parâmetro
elementoHTML.addEventListener("click", () => { 
  alert("Fui clicado")
})
```
### Para saber todos os tipos de eventos visite:
- [MDN - Referência de Eventos](https://developer.mozilla.org/pt-BR/docs/Web/Events)

## Objetos
### Criando Objetos no JavaScript
- Objetos JavaScript são a base para os arquivos JSON
- Objetos são conjuntos de dados normalmente definidos por pares: chave <-> valor
- Eles podem ser declarados de duas maneiras:

```javascript
let usuario = new Object() // Construtor de Objetos

let usuario = {} // Object Literal

```

- O mais usado normalmente é o Object Literal, que permite a adição de valores ja na declaração
- Podemos fazer, por exemplo:
```js
// Declaração já com pares chave <-> valor

let usuario = {
  nome: Pato,
  idade: 20,
  linguagem: "Quack", // Não tem problema essa "," no fim
};
```
#### Acessando e Manipulando Objetos
- Quando lidamos com objetos, temos duas notações principais:
  - A notação de ponto (dot notation): objeto.chave
  - E a notação de colchetes:          objeto["chave"]

```js

let propriedade = "poderesEspeciais"; // preste atenção nessa variável

let objeto = {
  nome: "Pato",                          
  propriedade: "ERRO",   // Isto criaria apenas uma variável com uma CHAVE
                         // "propriedade" e não usando a VARIAVEL propriedade
  
  
  // Quando usamos a notação de [] podemos usar
  // variaveis no lugar das "chaves" do objeto

  [propriedade]: "Voar, Nadar e Andar", // Esta declaração se transforma em:
                                // "poderesEspeciais": "Voar, Nadar e Andar"
};

// Da mesma maneira, não podemos acessar a chave "poderesEspeciais"
// usando a notação de ponto

objeto.propriedade  // ERRO
objeto[propriedade] // Voar, Nadar e Andar

```

- Quando não há necessidade de manipular variáveis nas chaves do objeto, é preferível o uso da "dot notation": objeto.chave

### Manipulando chaves de objetos
- Podemos verificar se uma chave existe em um objeto utilzando a palavra-chave **"in"**
- Usando esta mesma palavra chave, também podemos criar loops utilizando como base as chaves de um objeto:

```js
// Novo Objeto usuario com chaves: nome, apelido, senha
let usuario = {
  nome: "Joao",
  apelido: "Pato",
  senha: "hunter2",
}

if ("senha" in usuario){ // Checa se existe uma chave "senha" no Objeto usuario
  alert(`Sua senha é ${usuario.senha}`);
}

// Para iterar usando as chaves de um objeto
// Podemos usar as palavras-chave: "for... in"
for (let key in usuario){ // itera sobre cada chave
  console.log(`Chave: ${key} Valor: ${usuario[key]}`);
}
```
### Métodos e "this"

- No mundo real, os "objetos" podem, alem de conter dados, realizar ações
- Estas ações seriam funções que estão intrinsicamente ligadas aos objetos.
- Da mesma maneira, métodos são funções/ações contidas dentro de objetos JavaScript
- Temos o exemplo de um rádio:

```js
// Nosso Radio tem 5 watts de potência, 2 antenas
// e além disso pode tunar para qualquer canal FM

// Vamos criar um Rádio JavaScript :)
let radio = {
  potencia: 5,
  antenas: 2,
  canalAtual: 93.7, // Radio USP Capital

  tune: function(novoCanal){
    this.canalAtual = novoCanal;
    alert(`Novo canal que estamos escutando: ${this.canalAtual});
  },
}
```
- No exemplo anterior fizemos uma referência a uma propriedade do objeto dentro da função
- Para acessar o "canalAtual" dentro do objeto, precisamos usar a palavra-chave **this**
- **this** indica uma referência ao próprio objeto. Tentar acessar **canalAtual** sem o this resultara em um erro
- Para indicarmos que estamos buscando dentro do próprio objeto temos que o usar: **this.canalAtual**


### Funções Construtoras

- Por vezes, precisamos construir vários objetos idênticos, para isso temos as funções construtoras
- Nelas, podemos criar um molde de objeto que podem ser construidos ao executar a função
- Funções Construtoras são funções regulares, mas existe um consenso em iniciar o nome delas com letra maiúscula:

```js

const Usuario = function(nome, senha){
  this.nome = nome;
  this.senha = senha;
  this.administrador = false;

  console.log(`Novo usuario com nome ${this.nome} e senha ${this.senha}`)
};

/* É importante usar a palavra-chave "new" antes de chamar uma função construtora
   ela é necessária para o bom funcionamento de declarações com "this",
   entre outras coisas */
let joao = new Usuario("joao", "hunter2");
```

## JSON
### O que é JSON
- JSON se refere a **Notação de Objetos JavaScript**
- É um padrão de envio e leitura de dados
- É feito para ser legível para Humanos
- Usa como base, a estrura de objetos JavaScript, ou seja:
  - Funciona através de pares chave <-> valor
  - Pode armazenar qualquer tipo de informação
- Porém existem algumas diferenças, sendo as principais:
  - Não aceita funções de JavaScript como propriedade
  - Exige que as "chaves" do objeto fiquem entre aspas
  - Não pode ter comentários

### Exemplo:
```js
// A seguir um objeto JavaScript
let usuario = {

  dizOi() { // É uma função então será ignorada na transformação para JSON
    alert("Oi");
  },

  nome: "Joao",
  idade:  30,
  observacao: "Quem leu é lindo"
};

/* A seguir o objeto anterior, porém convertido para JSON
{
  // Função não existe mais

  // Chaves entre aspas
  "nome": "Joao",
  "idade":  30,
  "observacao": "Quem leu é lindo"
};
*/
```

### Codificando e Decodificando JSON

- Para codificar um objeto JavaScript para JSON temos a função JSON.stringfy():
  - ```stringJSON = JSON.stringfy(objetoJS);```
- Já para decodificar um JSON e usá-lo em nosso código temos a função JSON.parse():
  - ```objetoJS = JSON.parse(stringJSON);```



## Arrays
### O que são e declaração

- Arrays são um tipo especial de objeto que não tem uma chave nomeada, mas sim um índice
- Eles são definidos utilizando colchetes "[]", na seguinte forma:

```js

// Utilizando Índices, partindodo "0"

//                 [0]    [1]       [2]
let sequencia = ["Joao", "Pato", "Ortogonal"]; // Colchetes


// Podemos checar os índices de um array usando a notação de colchetes
```

- Arrays extendem a funcionalidade dos objetos simples, adicionando novos métodos específicos para arrays.

## Métodos para Arrays
### Adicionar e excluir membros de um array

- Para isso temos as seguintes funções:
  - array.pop() -> Remove o último item do array e retorna-o
  - array.push(item1, item2, ...) -> Adiciona items para o final do array
  - array.shift() -> Remove o primeiro item do array e retorna-o
  - array.unshift(item1, item2, ...) ->  Adiciona items no ínicio do array
- Estes 4 métodos lidam especificamente com o início e o fim do array, mas e o meio?
- Para isso temos dois métodos poderosos:

### Gerando um "subarray" com array.slice
  - array.slice(inicio, fim) -> Retorna um array começado em "inicio" e terminando em "fim" (porém sem incluir "fim")
```js
let array = [2, 4, 5, 7, 9, 11];

let novoArray = array.slice(2, 5);

alert(novoArray); // resultado do slice -> [5, 7, 9]
```
### Deletando e adicionando membros em um array através de índices com array.splice()
  - array.splice(índice, quantidadeParaDeletar, novoMembro1, novoMembro2, ...)
  - Este método escolhe um "índice" e deleta "quantidadeParaDeletar" a partir dele, opcionalmente ele adiciona os novos membros a partir do "índice"
  - Além disso, ele retorna todos os membros deletados
```js
let array = [2, 4, 5, 7, 9, 11];

let novoArray = array.splice(2, 3, "NovoMembro");
// Tradução: A partir do índice 2, delete 3 membros e adicione "NovoMembro"

alert(novoArray); // Membros deletados -> [5, 7, 9]

alert(array); // O restante, incluido o "NovoMembro" -> [2, 4, "NovoMembro", 11]
```

### Concatenando Arrays
- array.concat (Concatenar membros a um array)
- Adiciona os membros de um array2 a outro array1 (também pode juntar items adicionais )
```js
let array = [1, 2];

// Junta [3, 4] ao array inicial
alert( array.concat([3, 4]) ); // 1,2,3,4

// Junta dois arrays [3, 4] e [5, 6] ao array inicial
alert( array.concat([3, 4], [5, 6]) ); // [1,2,3,4,5,6]

// Junta [3, 4] e adiciona os items 5, 6 ao array inicial
alert( array.concat([3, 4], 5, 6) ); // [1,2,3,4,5,6]
```


### Ordenando Arrays
- Para ordenar um array temos as seguintes funções:
  - array.reverse() -> Reverte a ordem do array
  - array.sort(funcao); -> Ordena com base na função opcional
    - Como base, a função sort() ordena strings através da tabela ASCII
    - Porém podemos definr uma função de ordenação que ordene através de valores númericos, por exemplo
```js
let array = [22, 34, 12, 11, 47, 115];

array.sort() // 11, 115, 12, 22, 34, 47 -> Ordenação alfabética: 115 < 12

// Usando "(a, b) => a - b"  como função de apoio 
// teremos a versão numérica deste sort
array.sort((a, b) => a - b); // 11, 12, 22, 34, 47, 115
```

### Filtrando Arrays
 - array.filter(funcao) -> Usa uma função para filtrar o array de interesse, retornando um novo array apenas com os items que passaram pelo filtro
 
```js
let array = [22, 34, 12, 11, 47, 115];

// Exemplo, vamos filtrar apenas por items pares

// Usaremos como argumento de filter uma função que checa
// se o resto de uma divisão por 2 é 0 (checa se é par)
let arrayFiltrado = array.filter(
  function(item){
    if (item % 2 == 0)
      return item
});

alert(array); // [22, 34, 12, 11, 47, 115]

alert(arrayFiltrado); //  [22, 34, 12 ]
```

### Buscando dentro de Arrays:
- Para buscar dentro de um array temos duas funções complementares
  - array.includes(valor) -> Retorna true se o array possui um determinado valor e false se ele não possui
  - array.indexOf(valor) -> Retorna a posição de um determinado valor dentro do array. Se o array não possui tal valor, retorna -1

```js
// Pos:  0   1   2   3
let array = [11, 22, 34, 47];

// Existe um valor no array?
array.includes(11); // True
array.includes(13);// False

// Onde está determinado valor no array?
array.indexOf(22); // 1
array.indexof(13); // Não existe, portanto retorna -1
```

### Loops poderosos com array.forEach() & array.map()
#### A diferença é que map() retorna um novo array com as mudanças, ja o forEach() apenas executa uma função no array principal
- Executa uma função para cada elemento de um array
- A função executada recebe até três parâmetros
  - O elemento atual do array a ser modificado (OBRIGATORIO)
  - O indice deste elemento (OPCIONAL)
  - O array em que o elemento se encontra (OPCIONAL)
- Exemplo de uso:

```js
let array = [11, 12, 13, 14, 15, 16]

// Multiplica cada elemento do array por 3 e retorna um novo array usando map()
let novoArray = array.map(elemento => elemento * 3);

// Multiplica cada elemento do array por 2 usando forEach()
array.forEach((elemento, indice) => array[indice] = elemento * 2);

alert(array);
alert(novoArray);
```

## JavaScript Assíncrono
- Atualmente existem 3 métodos para lidar com JavaScript Assíncrono
  - Callbacks
  - Promises
  - Async - Await
- Discutiremos eles a seguir
#### Observação: Assincronia no JavaScript é um assunto relativamente complexo, portanto é interessante procurar várias fontes caso as ideias não estejam claras

### Callbacks
- Método mais antiquado
- Quando estamos lidando com funções demoradas (como uma requisição HTTP), temos dois problemas:
  - Não queremos parar a execução do resto do script
  - Ao mesmo tempo, precisamos ter certeza que a requisição foi finalizada para podermos acessar os conteúdos dela
- Ai surge a ideia do callback: Uma função que é chamada só depois da finalização desta nossa requisição

Exemplo: Pegar a localização geográfica de um usuário
```js

// Callback em caso de sucesso
function success(pos) {
  let crd = pos.coords;

  console.log('Sua posição atual é:');
  console.log('Latitude : ' + crd.latitude);
  console.log('Longitude: ' + crd.longitude);
  console.log('Mais ou menos ' + crd.accuracy + ' metros.');
};

// Callback em caso de erro
function error(err) {
  console.warn('ERROR(' + err.code + '): ' + err.message);
};

// Função assíncrona, visto que pode demorar para 
// conseguirmos a localização do usuário por GPS
navigator.geolocation.getCurrentPosition(success, error)
```
- Em geral, Callbacks são um modo nada intuitivo de resolver problemas relacionados a assincronia
- Por isso, novos métodos para requisições assíncronas foram criados

### Promises (Promessas)
- Promises são uma maneira de executar código assincrono baseada na subscrição de funções
- Imagine o seguinte:
  - Existe um canal do youtube que da aulas de Introdução a Computação
  - Você esta inscrito neste canal
  - Quando você ver o video do canal, estará apto a fazer uma nova lição de casa que envolve um novo conteúdo
- Nesta analogia temos:
  - O canal do youtube seria uma Promise, que quando está pronta retorna um video novo
  - Você é um "Consumidor" desta Promise, pois precisa dela para executar o novo exercício
  - Enquanto a Promise não está pronta, você segue com a sua vida (a execução do Código)
  - Quando ela finaliza, você "consome" ela e realiza o exercícico proposto
- Exemplos em código:

#### Criando Promises
```js
// Na Promise, temos um Resolve e um Reject
// Resolve -> Resultado bom, é usado nos consumidores ".then"
// Reject -> Resultado Ruim, é usado nos consumidores ".catch"
// Logo entenderemos mais profundamente os consumidores

let videoDoYoutube = new Promise( (resolve, reject) => {
  // Depois de um timer de 5 segundos, o video fica pronto através do resolve
  setTimeout(() => resolve("Video Prontinho, poderei fazer a lição"), 5000);

  // Se o vídeo não ficar pronto, Definimos um novo erro usando "new Error"
  // Este erro será utilizado pelo .catch (Que define o que fazer em caso de erros)
  reject(new Error("Vídeo não ficou pronto até o fim do prazo do trabalho"));
});
```
#### Consumindo Promises

- Para consumir promessas, usamos 3 métodos específicos para Promises
  - promise.then(funcao) -> Define o que fazer quando a Promise é "resolvida" com o resolve
  - promise.catch(funcao) -> Define o que fazer quando uma promise é "rejeitada" com o reject
  - promise.finally(funcao) -> Executa uma função independete da Promise ser "rejeitada" ou "resolvida"

```js
// Usando a promise definida anteriormente:

videoDoYoutube
.then(resultado => {
  alert(resultado);
})
.catch( erro => {
  alert(erro);
})
.finally( () => {
  alert("Independente de ver o vídeo ou não, fiz o meu melhor");
})
```

### Async-Await
- Async-Await é uma outra maneira de se lidar com Promises
- A palavra-chave **async** antes de qualquer função simboliza que a função retornará uma Promise
  - Se o conteúdo de uma função for síncrono, o async "envolve" este conteúdo em uma Promise (que terá retorno imediato)
- A palavra-chave **await** funciona dentro de funções definidas com async
  - Quando uma declaração de Promise é precedida por **await**, o código de dentro da função pausa e espera o retorno da Promise
Exemplo de uso conjunto de async-await

```js
async function funcao() {

  let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("Finalizado!"), 1000)
  });

  let resultado = await promise; // Espera até que a Promise anterior
                                 // seja resolvida

  alert(resultado); // Com o await, poderemos ter certeza de que o 
                    // resultado já foi declarado antes de usá-lo
}

funcao(); // chamada da função assíncrona
alert("Executei antes ou depois?")
```

- Dica: Tente copiar o código acima rodar no console, depois retire o "await" e tente novamente para entender o funcionamento de funções assíncronas


## Módulos
- Quando nossas aplicações ficam grandes, é interessante começar a dividí-las em múltiplos arquivs
- Um módulo é um desses arquivos, normalmente contem uma classe de objeto ou uma biblioteca de funções
- A sintaxe oficial do EcmaScript 2015

### Export e Import
- Como módulos são uma maneira de comunicação entre arquivos criaremos 2 arquivos
  - Um que cria e exporta funções: export.js
  - Outro que importa, e as utiliza: import.js

export.js 
```js
// Podemos exportar durante a declaração
export function barulhoDoPato() {
  alert("QUACK QUACK QUACK");
}

export function barulhoDoBoi() {
  alert("MUUUUUUUUUUUUUUH");
}

// Ou no final do projeto usando a sintaxe a seguir:
export {barulhoDoPato, barulhoDoBoi};
```

import.js
```js
// Para importar uma função a sintaxe é a seguinte
import {barulhoDoBoi, barulhoDoPato} from "./import.js";

barulhoDoPato();

```
#### OU
```js
// Também podemos importar um módulo inteiro
// dando um nome a ele da seguinte maneira:
import * as barulhos from "./import.js";

// Usando essa sintaxe podemos chamar a função usando a notação de .:
barulhos.barulhoDoPato();
```
- Existe uma outra sintáxe que é normalmente usada no node.js:
```js 
const modulo = require("./import.js"); 
```
## Requests usando Axios
- Para finalizar vamos falar de um assunto mais prático:
  - Como realizar requisições usando Axios
### O que é Axios
- É um cliente de requisições HTTP
- Pode ser usado tanto nos navegadores quanto no node.js
- É baseado em Promises
- Transforma automaticamente os dados JSON que você quer receber em Objetos Javascript e vice-versa

### Como inserí-lo no seu projeto
- Primeiramente deve-se criar um projeto usando o npm/npx
- Após isso, dentro da pasta do projeto execute o comando: ```npm install axios```

### Exemplo de uso de Axios
- Passos para usar o Áxios:
  1) Importar o módulo do axios
  2) Preparar uma configuração do nosso request
  3) Lidar com a Promise gerada pelo axios


```js
const axios = require('axios'); // Importando o módulo do axios

// A seguir a configuração da nossa Requisição

const configuracao = {
  method: 'post', // Método da Requisição
  // URL onde a Requisição será realizada
  url: 'https://jsonplaceholder.typicode.com/posts',  
  data: {  // Dados que devem ser enviados na Requisição
    firstName: 'Fred',
    lastName: 'Flintstone'
  }
};

// Agora, fazemos a chamada do Axios e lidamos com a resposta assíncronamente

axios(configuracao)
.then( resposta => {
  console.log(resposta.data) // Mostra o resultado da Resposta no console
})
.catch( erro => { // Em caso de erro, console.log(erro)
  console.log(erro) 
});
```
- Em caso de dúvidas, acesse a [Documentação Oficial do Axios no GitHub](https://github.com/axios/axios)



