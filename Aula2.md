# Resumo Aula 02 do Explorer Lab 01

## Teoria

- Biblioteca iMask

  - cria máscaras de input no JavaScript (formatação de campos)
  - npm install imask

- Regex
  - forma de identificar padrões em um conteúdo

## Código

-> pegamos o cvc do cc com o `querySelector`
-> fizemos uma máscara de no máximo 4 dígitos com o imask

-> pegamos a data de expiração do cc com o `querySelector`
-> fizemos uma máscara mais complexa usando `blocks` do imask
-> os primeiros 2 dígitos irem até 12 (mês), e os últimos 2 dígitos serem o ano atual + 10 para simular uma validade, dividos por uma `/`

-> pegamos o número do cartão com o `querySelector`
-> criamos uma dynamicMask utilizando expressões regulares para cada tipo de cartão (visa, mastercard...)
-> para usar este tipo de máscara temos que usar a propriedade `dispatch`
-> é uma função que executa sempre que digitarmos um número
-> faz uma filtragem de dados (apenas dígitos)
-> e busca no array se o item digitado confere com o regex de algum cc
-> por fim retorna o `cardtype`

# Expressões Regulares (Regex com JavaScript)

- Busca padrão dentro de um texto

- Forma de identificar padrões em um conteúdo

## Criando regex no JavaScript

```js
// dentro das "/" terá uma expressão regular
// se lê -> procure um "f" seguido de um "o", seguido de outro "o"
const re = /foo/

const re = new RegExp(/foo/)
```

## Funções usadas em Strings

```js
// agrupa os padrões em um array
// procure todos os caracteres maiúsculos de A até Z | "g"  =  padrões das expressões regulares (global, busca no texto todo)
const matches = "aBC".match(/[A-Z]/g);
// Output: Array [B, C]

// pesquisa se existe ou não o padrão
const index = "aBC".search(/[A-Z]/);
// Output: 1

// substitui os padrões por novo valor
const next = "aBC".replace(/a/, "A")/
// Output: ABC
```

## Cheatsheet

### Básico

- `/ expression / flags `
  Exemplo: /[A-Z]+/g

- `\` = usar caracteres especiais
  ExemplO: / Oi\?\*\\ /

- `()` = agrupador
- `|` = OU lógico
- `Fala Dev` = pesquisa exata
- `^Fala` = pesquisa começa com
- `Dev$` = pesquisa termina com

### Colchetes

- [xyz] = qualquer um x, y, z
- [J-Z] = qualquer caracter entre J e Z
- [^xyz] = nenhum x, y, z

### Classe de caracteres

- `\w` = todas as palavras | `\d` = todos os dígitos | `\s` = espaços em branco (tabs, quebras de linha)

- `\W` = NÃO palavra | `\D` = NÃO dígito | `\S` = NÃO espaços em branco

- `\t` = tabs | `\n` = quebra de linha

- `.` = qualquer caracter (exceto nova linha)

- `mayk|diego` = mayk ou diego

- `?` zero ou uma ocorrência

- `*` zero ou múltiplas ocorrências

- `+` uma ou múltiplas ocorrências

- `{n}` n ocorrências

- `{min, max}` mínima/máxima ocorrências

# Regras dos Cartões

## Visa

- Inicia com o número "4" seguido de mais 15 dígitos
  Ex: 4234234423432344

-> para achar com expressão regular = `/^4\d{0,15}/`

## MasterCard

- Inicia com "5", seguido de um dígito entre "1" e "5", seguido de mais 2 dígitos
  -> `^5[1-5]\d{0,2}`

OU -> `|`

- Inicia com "22", seguido de um dígito entre "2" e "9", seguido de mais 1 dígito
  -> `^22[2-9]\d`

OU -> `|`

- Inicia com "2", seguido de um dígito entre "3" e "7", seguido de mais 2 dígitos
  -> `^2[3-7]\d{0,2}`

- Seguido de mais 12 dígitos
  -> `\d{0,12}`

  Ex: 5353535353535353 | 2323232323232323

-> com expressão regular = `/(^5[1-5]\d{0,2}|^22[2-9]\d|^2[3-7]\d{0,2})\d{0,12}/`

# Referências

- https://imask.js.org/guide.html
- https://fireship.io/lessons/regex-cheat-sheet-js/
- https://www.debuggex.com/cheatsheet/regex/javascript
