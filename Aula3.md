# Resumo Aula 03 do Explorer Lab 01

## Manipulação de Eventos da DOM

- Evento = ação que acontece a partir da interação do usuário

### Clique do botão

- usamos `querySelector` para pegar a id do button
- adicionamos um evento `addEventListener` na funcionalidade `click`, que ao clicar no botão ele nos mostra um alerta `alert`

### Desativando o reload do submit

- pegamos o formulário onde o botão está inserido (`querySelector`)
- pegamos a funcionalidade "submit" e usamos `document.preventDefault` (o comportamento padrão é reinicializar a página)

### Obtendo e exibindo o nome do titular

- pegamos o id do input `card-holder` pelo `querySelector`
- adicionamos um evento `addEventListener` na funcionalidade `input`
- criamos uma `arrow function` que pega o valor do titular no cartão (fulano da silva)
- então fazemos um "if ternário"

  - usamos a funcionalidade `.innerText` para pegarmos o texto digitado no campo

    - `ccHolder.innerText`

  - se o tamanho do conteúdo for igual a 0, entao mostramos "FULANO DA SILVA"

    - (`cardHolder.value.length === 0 ? "FULANO DA SILVA"`)

  - se não, mostramos o valor do input

    - `: cardHolder.value`

  - e o resultado disso fica guardado na imagem do cartão

    - `ccHolder.innerText`

## Eventos do IMask

### Obtendo e exibindo o CVC do cartão

- mesma lógica do nome do titular
- porém agora usamos a máscara do input que fizemos `securityCodeMasked`
- com a funcionalidade `.on` (mesma lógica do `addEventListener`)
- com o parâmetro `accept` (se aceita a condição da máscara)

- construimos uma função `updateSecurityCode` com o parâmetro `code`

  - que pega o valor do cartão e faz o if ternário

- depois só passamos a função com o valor da máscara criada

### Obtendo e exibindo o número do cartão

- mesma lógica do cvc

- porém agora temos que mostrar o tipo do cartão

  - pra isso criamos uma const `cardType` que pega o valor do cartão

    - cardNumberMasked.masked.currentMask.cardtype

    - e então usamos a função já criada `setCardType()` e passamos o `cardType` como parâmetro

### Obtendo e exibindo a data do cartão

- mesma lógica dos últimos dois
