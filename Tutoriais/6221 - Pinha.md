# Jogo da Pinha

## Sobre o jogo
O jogo da pinha é um jogo em que o jogador deve clicar no botão A no exato momento que um ponto (sprite) passar pelo centro da tela.

## Criando nosso sprite
Vamos iniciar a programação do nosso jogo criando o nosso sprite, que deve desviar das pinhas!

1. Na categoria ``||variables:Variáveis||``, clique em **"Fazer uma variável..."** e chame-a de ``||variables:Sprite||``
2. Arraste o bloco ``||variables:definir Sprite para(0)||`` (``||variables:Variáveis||``) para dentro do bloco ``||basic:no iniciar||``
3. Na categoria ``||game:Jogo||`` (Avançado), pegue o bloco ``||game:criar sprite em x: (2) y:(2) ||`` e coloque-o dentro do bloco ``||variables:definir sprite para(0)||`` substituindo o **0**
4. Altere o valor de Y para 4 para que fique ``||game:criar sprite em x: (2) y:(4) ||``

```blocks
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
```

## Criando nossas pinhas
Agora iremos criar as nossas pinhas que irão cair do céu.

1. Faça o mesmo processo para criar uma variável chamada `||variables:Pinha||``
2. Arraste o bloco ``||variables:definir Pinha para(0)||`` (``||variables:Variáveis||``) para dentro do bloco ``||basic:no iniciar||``
3. Na categoria ``||game:Jogo||`` (Avançado), pegue o bloco ``||game:criar sprite em x: (2) y:(2) ||`` e coloque-o dentro do bloco ``||variables:definir sprite para(0)||`` substituindo o **0**
4. Altere o valor de Y para 0 para que fique ``||game:criar sprite em x: (2) y:(0) ||``
5. Na categoria ``||math:Matemática||``, insira o bloco ``||math:escolher aleatório (0) até (10)||`` no valor de X no bloco ``||game:criar sprite em x: (2) y:(0) ||``
6. Atualize o valor do bloco para que ele fique ``||math:escolher aleatório (0) até (4)||`` 

```blocks
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
let pinha = game.createSprite(randint(0, 4), 0)
```

## Definindo a pontuação
 Vamos iniciar o nosso contador da pontuação:

1. Na categoria ``||game:Jogo||`` (Avançado), pegue o bloco ``||game:definir pontuação (0)||`` e coloque-o no final do bloco ``||basic:no iniciar||``

 ```blocks
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
let pinha = game.createSprite(randint(0, 4), 0)
game.setScore(0)
```



## Movimentando o sprinte - A 
Vamos configurar a movimentação do nosso personagem para a esquerda

1. Na categoria ``||input:Entrada||``, arraste o bloco ``||input:no botão A pressionado||`` para o nosso código
2. Arraste o bloco ``||game:(sprite) mover por (1)||``(``||game:Jogo||``)
3. Atualize o valor do mover para que fique ``||game:(sprite) mover por (-1)||``



```blocks
input.onButtonPressed(Button.A, function () {
    sprite.move(-1)
})
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
let pinha = game.createSprite(randint(0, 4), 0)
game.setScore(0)
```

## Movimentando o sprinte - B 
Agora vamos configurar a movimentação do nosso personagem para a direita

1. Arraste o bloco ``||input:no botão A pressionado||`` para o nosso código e altere para o botão B, de modo que fique ``||input:no botão B pressionado||``
2. Arraste o bloco ``||game:(sprite) mover por (1)||``(``||game:Jogo||``)



```blocks
input.onButtonPressed(Button.A, function () {
    sprite.move(-1)
})
input.onButtonPressed(Button.B, function () {
    sprite.move(1)
})
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
let pinha = game.createSprite(randint(0, 4), 0)
game.setScore(0)
```


## Configurando a pinha
Com os atores do nosso jogo e sua movimentação configurados, vamos partir para a lógica do jogo! Para isso, iremos montar as próximas aprtes do código dentro do bloco ``||basic:sempre||``.

Vamos começar configurando a nossa pinha, para que ela desça aos poucos.

1. Arraste o bloco ``||basic:pausa (ms) (100)||`` e altere o seu valor para 200 ms (``||basic:pausa (ms) (200)||``) 
2. Da categoria ``||game:Jogo||``, Arraste o bloco ``||game:(sprite) alterar (x) por (1)||`` e atualize-o para que fique com os valores: ``||game:(pinha) alterar (y) por (1)||``



```blocks
input.onButtonPressed(Button.A, function () {
    sprite.move(-1)
})
input.onButtonPressed(Button.B, function () {
    sprite.move(1)
})
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
let pinha = game.createSprite(randint(0, 4), 0)
game.setScore(0)
basic.forever(function () {
    basic.pause(200)
    pinha.change(LedSpriteProperty.Y, 1)
})
```


## Se
Está na hora de criarmos a lógica do nosso jogo, para isso, vamos configurar uma condição para que o jogador perca quando a pinha cair em cima do seu personagem!

Para isso, adicione os seguintes blocos no final do bloco ``||basic:sempre||``.

1. Adicione o bloco ``||logic:se (verdadeiro) então...||`` da categoria ``||logic:Lógica||``
2. Agora iremos definir uma condicional para o nosso bloco, para isso iremos utilizar o bloco ``||game:is (sprite) touching ()||`` (``||game:Jogo||``)
3. Com a nossa condicional no lugar, vamos definir o que o nosso personagem deve estar tocando para perder, que é a nossa Pinha! Para isso, adicione o bloco ``||variables:pinha||`` para que a condicional fique ``||game:is (sprite) touching (pinha)||``
4. Por último vamos confiurar o que deve acontecer dentro do nosso "Se", com o bloco ``||game:fim do jogo||``


```blocks
input.onButtonPressed(Button.A, function () {
    sprite.move(-1)
})
input.onButtonPressed(Button.B, function () {
    sprite.move(1)
})
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
let pinha = game.createSprite(randint(0, 4), 0)
game.setScore(0)
basic.forever(function () {
    basic.pause(200)
    pinha.change(LedSpriteProperty.Y, 1)
    if (sprite.isTouching(pinha)) {
        game.gameOver()
    }
})
```


## Pinhas no chão
Agora vamos fazer as nossas pinhas cairem! Para tal, devemos identificar quando a nossa pinha toca o chão.

Para isso, adicione os seguintes comandos no bloco ``||basic:sempre||``:

1. Adicione o bloco ``||logic:se (verdadeiro) então...||``
2. Para definir a nossa nova condicional iremos utilizar o bloco ``||logic:(0) = (0)||``
3. Logo em seguida, abra a categora ``||game:Jogo||`` e pegue o bloco ``||game:(sprite)) (x)||`` e o adicione no lado esquerdo do nosso bloco ``||logic:(0) = (0)||`` e altere os parâmetros para que fique ``||logic:((sprite)) (y)) = (4)||``


```blocks
input.onButtonPressed(Button.A, function () {
    sprite.move(-1)
})
input.onButtonPressed(Button.B, function () {
    sprite.move(1)
})
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
let pinha = game.createSprite(randint(0, 4), 0)
game.setScore(0)
basic.forever(function () {
    basic.pause(200)
    pinha.change(LedSpriteProperty.Y, 1)
    if (sprite.isTouching(pinha)) {
        game.gameOver()
    }
    if (pinha.get(LedSpriteProperty.Y) == 4) {
    
    }
})
```

## Deletando pinhas
Agora que identificamos quando a pinha chega ao chão, vamos a deletá-la. Para isso, adicione os seguintes comandos no bloco ``||basic:sempre||``:

1. Adicione o bloco ``||game:delete(sprite)||`` e altere o seu parâmetro para que fique ``||game:delete(pinha)||`` dentro nosso último se (``||logic:((sprite)) (y)) = (4)||``)


```blocks
input.onButtonPressed(Button.A, function () {
    sprite.move(-1)
})
input.onButtonPressed(Button.B, function () {
    sprite.move(1)
})
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
let pinha = game.createSprite(randint(0, 4), 0)
game.setScore(0)
basic.forever(function () {
    basic.pause(200)
    pinha.change(LedSpriteProperty.Y, 1)
    if (sprite.isTouching(pinha)) {
        game.gameOver()
    }
    if (pinha.get(LedSpriteProperty.Y) == 4) {
        pinha.delete()
    }
})
```


## Criando mais pinhas
Chegou o momento de criarmos nossas novas pinhas! Para isso, siga os passos dentro do nosso último ``||logic:((sprite)) (y)) = (4)||``.

1. Da categoria ``||variables:Variáveis||``, adicione o bloco ``||variables:definir (pinha) para (0)||``
2. Adicione o bloco ``||game:criar sprite em x:(2) y:(2)||`` dentro do bloco ``||variables:definir (pinha) para (0)||`` para que ele fique ``||variables:definir (pinha) para (criar sprite em x:(2) y:(2))||``
3. Altere o valor do bloco ``||game:criar sprite em x:(2) y:(2)||`` para que ele fique ``||variables:definir (pinha) para (criar sprite em x:(2) y:(0))||``
4. use o bloco ``||math:escolher aleatório de (0) até (10)||`` (``||math:Matemática||``) dentro do bloco ``||variables:definir (pinha) para (criar sprite em x:(2) y:(0))||`` para que ele fique ``||variables:definir (pinha) para (criar sprite em x:(escolher aleatório de (0) até (10)) y:(0))||``
5. Por fim, altere os parâmetros do bloco ``||math:escolher aleatório de (0) até (10)||`` para ``||math:escolher aleatório de (0) até (4)||``


```blocks
input.onButtonPressed(Button.A, function () {
    sprite.move(-1)
})
input.onButtonPressed(Button.B, function () {
    sprite.move(1)
})
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
let pinha = game.createSprite(randint(0, 4), 0)
game.setScore(0)
basic.forever(function () {
    basic.pause(200)
    pinha.change(LedSpriteProperty.Y, 1)
    if (sprite.isTouching(pinha)) {
        game.gameOver()
    }
    if (pinha.get(LedSpriteProperty.Y) == 4) {
        pinha.delete()
        pinha = game.createSprite(randint(0, 4), 0)
    }
})
```


## Contando pontos
Para finalizar o nosso projeto, vamos criar o nosso contador de pontos! Para isso, siga os passos:

1. Adicione o bloco ``||game:alterar pontuação em (1)||`` abaixo do nosso bloco ``||variables:definir (pinha) para ...``


```blocks
input.onButtonPressed(Button.A, function () {
    sprite.move(-1)
})
input.onButtonPressed(Button.B, function () {
    sprite.move(1)
})
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
let pinha = game.createSprite(randint(0, 4), 0)
game.setScore(0)
basic.forever(function () {
    basic.pause(200)
    pinha.change(LedSpriteProperty.Y, 1)
    if (sprite.isTouching(pinha)) {
        game.gameOver()
    }
    if (pinha.get(LedSpriteProperty.Y) == 4) {
        pinha.delete()
        pinha = game.createSprite(randint(0, 4), 0)
        game.addScore(1)
    }
})
```





## {Finalizado}

Chegou a grande hora! Vamos testar o nosso jogo. Primeiro teste o jogo no preview do micro:bit no lado esquerdo da tela.

Com o jogo finalizado e funcionando, conecte seu micro:bit, clique em ``|Baixar|`` e siga os passos apresentados.

Divirta-se e melhore o seu jogo!
