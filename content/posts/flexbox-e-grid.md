---
title: "Flexbox e Grid"
date: 2020-04-30T22:51:37-03:00
lastmod: 2020-04-30T22:51:37-03:00
tags : [ "dev", "flexbox", "grid", "css"]
categories : [ "dev" ]
layout: post
type:  "post"
highlight: false
draft: false
---

# Posicionando Com Flexbox e Grid
## Indíce

### Flexbox
  - [Background](#sobre-o-flexbox)
  - [Container](#flex-container)
  - [Itens](#flex-items)

### Grid
  - [Background](#sobre-o-grid)
  - [Container](#grid-container)
  - [Itens](#grid-items)

## Bibliografia

### [Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
### [Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

## Flexbox

### Sobre o Flexbox

- Habilita um container a alterar a largura e comprimento dos itens dentro dele
- Direção Principal = Main
- Direção Secundária = Cross 
- Depende da propriedade flex-direction

### Flex Container

#### Definições do container flex
  - display: flex;
- flex-direction: Direção e sentido principais
  - row / row-reverse
  - column / column-reverse
- flex-wrap: Todos os items devem ficar na mesma linha, ou devem ir pra próxima em caso de falta de espaço?
  - nowrap: mesma linha
  - wrap: vão pra prox linha
  - wrap-reverse: vão pra prox linha, começando da parte de baixo

#### Espaçamento e Alinhamento
- justify-content: **DEFINE O POSICIONAMENTO NO MAIN AXIS**
  - flex-start: containers começam do início
  - flex-end: containers começam no fim
  - center: centralizado
  - space-between: maior espaçamento, com o primeiro item no inicio e o último no fim
  - space-around: Um pouco de espaço em relação a borda, parecido com space-between
  - space-evenly: distribuição usando margens na esquerda e direita idênticas
- align-items: **DEFINE ESPAÇAMENTO NO CROSS AXIS**
  - flex-start: Inicio
  - flex-end: Fim
  - center: centralizado
  - stretch: Estica para cobrir o container inteiro
  - baseline: usa a "baseline" textual
- align-content: **DEFINE ESPAÇAMENTO NO CROSS AXIS ENTRE OS ITENS**
  - **Funciona se tiver mais de uma linha de itens flex**
  - flex-start: itens o mais próximo possível do início
  - flex-end: itens o mais próximo possível do fim
  - center: items o mais centralizado possível
  - space-between: espaçamento entre os itens
  - Etc... (mesmos do jstify-content)

### Flex Items

#### Ordenação
- flex-order: Define uma ordem de posicionamento
  - menores números sempre vem antes, independente da posição do CSS

#### Tamanho
- flex-grow: Valor unitário que determina a porcentagem que um item deve crescer em relação aos outros
- flex-shrink: Valor unitário que determina a porcentagem que um item deve diminuir em relação aos outros
- flex-basis: Tamanho inicial do item, antes da expansão / deflação tomar efeito

#### Alinhamento
- align-self: Substitui o alinhamento definido no container
  - usaos mesmos atributos
- Note: As propriedades **float, clear, vertical-align** não tem efeito em itens flex


## Grid

### Sobre o Grid
- Sistema com duas dimensões
- Funciona em todos os browsers
  - Menos IE11 (Porém funciona com algumas soluções)
- Terminologia
  - Grid Container: Container que dá propriedades de Grid para todos os seus filhos
  - Grid Item: Itens capazes de utilizar propriedades Grid
  - Grid Line: Linha da "matriz" que compõe o Grid
  - Grid Cell: Um quadrado ou célula, dentro da matriz
  - Grid Track: 

### Grid Container

#### Declarando o Grid Container
- Para iniciar uma grid usamos display: grid | inline-grid
- Para definir a disposição da grid usamos:
  - grid-template-columns: 50px 50px auto; Colunas da Grid
  - grid-template-rows: 30% 40% 50px auto; Linhas da Grid
  - Pode se nomear explicitamente cada uma das linhas e colunas:
    - grid-template-rows: [primeira-linha] 30% [seg-linha] 350px [terc-linha] auto [linha-final];
  - fr -> Espaço Livre, podemos usar para definir o tamanho das linhas como uma fração do espaço livre
    - grid-template-columns: 1fr 100px 100px 1fr -> Primeira e ultima coluna com metade do espaço livre cada
- Para definir a área de uma Grid temos:

```css
.item-a {
  grid-area: navbar;
}

.item-b {
  grid-area: footer;
}

.container {
  grid-template-columns: 1fr 2fr 1fr;
  grid-template-rows: 30% 20% 50%;
  grid-template-areas: 
    "navbar navbar navbar"
    ". .. ... ...." // Ignorado pela Grid Area
    "footer footer footer";
}
```

#### Gaps
- column-gap: Espaço entre as Colunas
- row-gap: Espaço entre as Linhas
- Pode se usar tbm o **gap**
  - gap: <linha> <coluna> 

#### Alinhando os itens
- **Serve para relacionar os ELEMENTOS com a GRID AREA**
- justify-items: start | end | stretch | center
  - Justifica os itens dentro de cada linha, usando umas das quatro propriedades acima
- align-items: start | end | strecth | center
  - Alinha os itens dentro de cada coluna, usa as mesmas quatro propriedades
- place-items: align / justify

#### Alinhando o conteúdo da Grid
- **Serve para relacionar as GRID AREAS com a GRID**
- justify-content: start | end | center | stretch | space-around | space-between | space-evenly
  - Justifica as Grid Áreas em relação a Grid, de maneira horizontal usa as mesmas propriedades que o flexbox
- align-content: start | end | center | stretch | space-around | space-between | space-evenly
  - Alinha as Grid Áreas em relação a Grid, de maneira vertical. Usa as mesmas props. que o flexbox
- place-content: align / justify 
  - Determina as duas propriedades anteriores em uma só declaração

### Grid Items
- **Observação:**
  - float, display: inline-bloc, display: table-cell, vertical-align e column-* não tem efeito em um Grid Item

#### Posicionando cada item na Grid

- grid-column-start & grid-column-end 
- grid-row-start & grid-row-end
  - Recebe a posição inicial e final do item dentro da Grid
  - Para definir essas posições podemos usar
    - Número da coluna / linha(span opcional)
    - Nome da coluna / linha (span opcional)
    - span <-numero-> indica que é pra passar por <-numero-> áreas, sendo elas colunas ou linhas
- Podemos usar os shorthands
  - grid-column: start / end
  - grid-row: start / end

#### Usando Grid Areas
- Duas utilidades
  - Shorthand das quatro funções mencionadas acima:
    - grid-area: row-start / column-start / row-end / column-end
  - Usado em conjunto com o grid-template-areas
    - grid-area: <-nome-area->

#### Alinhamento
- Podemos sobrescrever as definições do Grid Container usando
  - justify-self: start | end | center | stretch
  - align-self: start | end | center | stretch
  - place-self: align / justify


