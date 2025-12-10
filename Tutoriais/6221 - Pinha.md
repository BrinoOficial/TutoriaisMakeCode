# Jogo da Pinha

## Sobre o jogo
O jogo da pinha é um jogo em que o jogador deve clicar no botão A no exato momento que um ponto (sprite) passar pelo centro da tela.

## {Criando nosso sprite}
Vamos iniciar a programação do nosso jogo criando o nosso sprite, que deve desviar das pinhas!

1. Na categoria ``||variables:Variáveis||``, clique em **"Fazer uma variável..."** e chame-a de ``||variables:Sprite||``.
2. Arraste o bloco ``||variables:definir Sprite para(0)||`` (``||variables:Variáveis||``) para dentro do bloco ``||basic:no iniciar||``.
3. Na categoria ``||game:Jogo||`` (Avançado), pegue o bloco ``||game:criar sprite em x: (2) y:(2) ||`` e coloque-o dentro do bloco ``||variables:definir sprite para(0)||`` substituindo o **0**. 
4. Altere o valor de Y para 4 para que fique ``||game:criar sprite em x: (2) y:(4) ||``

```blocks
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
```

## {Criando nossas pinhas}
Agora iremos criar as nossas pinhas que irão cair do céu.

1. Faça o mesmo processo para criar uma variável chamada `||variables:Pinha||``.
2. Arraste o bloco ``||variables:definir Pinha para(0)||`` (``||variables:Variáveis||``) para dentro do bloco ``||basic:no iniciar||``.
3. Na categoria ``||game:Jogo||`` (Avançado), pegue o bloco ``||game:criar sprite em x: (2) y:(2) ||`` e coloque-o dentro do bloco ``||variables:definir sprite para(0)||`` substituindo o **0**. 
4. Altere o valor de Y para 0 para que fique ``||game:criar sprite em x: (2) y:(0) ||``
5. Na categoria ``||math:Matemática||``, insira o bloco ``||math:escolher aleatório (0) até (10)||`` no valor de X no bloco ``||game:criar sprite em x: (2) y:(0) ||``
6. Atualize o valor do bloco para que ele fique ``||math:escolher aleatório (0) até (4)||`` 

```blocks
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
let pinha = game.createSprite(randint(0, 4), 0)
```

## {Definindo a pontuação}
 Vamos iniciar o nosso contador da pontuação:

1. Na categoria ``||game:Jogo||`` (Avançado), pegue o bloco ``||game:definir pontuação (0)||`` e coloque-o no final do bloco ``||basic:no iniciar||``. 

 ```blocks
let sprite: game.LedSprite = null
sprite = game.createSprite(2, 4)
let pinha = game.createSprite(randint(0, 4), 0)
game.setScore(0)
```



## {Movimentando o sprinte - A} 
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

## {Movimentando o sprinte - B} 
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


















## {Criando Variáveis}
1. Arraste o bloco ``||math:escolher aleatório||`` para o **x** de onde será criada a ``||variable:Pinha||``.  
2. No bloco ``||math:escolher aleatório||``, mude o segundo número para **4**.  

```blocks
let Pinha = game.createSprite(randint(0, 4), 0)
let Sabrina = game.createSprite(2, 4)
```

## {Movimentação}
1. Adicione o bloco ``||input:no botão B pressionado||``.  
2. Dentro dele, adicione o bloco ``||game:Sabrina mover por 1||``.  
Assim, com **B**, conseguimos nos movimentar para a **direita**.

```blocks
let Sabrina = game.createSprite(2, 4)
input.onButtonPressed(Button.B, function () {
    Sabrina.move(1)
})
```

## {Movimentação}
1. Adicione o bloco ``||input:no botão A pressionado||``.  
2. Dentro dele, adicione o bloco ``||game:Sabrina mover por -1||``.  
Assim, com **A**, conseguimos nos movimentar para a **esquerda**.

```blocks
let Sabrina = game.createSprite(2, 4)
input.onButtonPressed(Button.A, function () {
    Sabrina.move(-1)
})
```

## {Movimentação}
1. Dentro de um bloco ``||basic:sempre||``, adicione o bloco ``||basic:pausa 500(ms)||``.  
2. Logo abaixo, adicione o bloco ``||game:Pinha alterar y por 1||``.

```blocks
let Pinha = game.createSprite(randint(0, 4), 0)
basic.forever(function () {
    basic.pause(500)
    Pinha.change(LedSpriteProperty.Y, 1)
})
```

## {Colisão}

A ``||variables:Sabrina||`` precisa **desviar** das ``||variables:Pinhas||``, para isso:  
1. Dentro do bloco ``||basic:sempre||``, logo abaixo do bloco de ``||game:alterar||``, adicione o bloco ``||logic:se... então||``.  
2. A condição do ``||logic:se||`` deve ser ``||game:is Sabrina touching||``
2. E adicionar o bloco ``||game:fim do jogo||`` no ``||logic:se||``.

```blocks
basic.forever(function () {
    if (Sabrina.isTouching(Pinha)) {
        game.gameOver()
    }
})
```

## {Pontuação}

Vamos aumentar os pontos quando a ``||variables:Pinha||`` chegar na última linha:
1. Dentro de ``||basic:sempre||``, adicione **outro** ``||logic:se||``.  
2. A condição deve ser um **bloco de comparação de igualdade** (``==``) que está em ``||logic:Lógica||``.

```blocks
basic.forever(function () {
    if (0 == 0) {
        
    }
})
```

## {Resetar a Pinha}
1. Troque o primeiro **0** por ``||game:sprite x||``.  
2. Mude **sprite** para ``||variables:Pinha||`` e troque **x** por **y**.  
3. Troque o segundo **0** por **4**.  
Assim o jogo verifica se o **y** da ``||variables:Pinha||`` está na linha **4** (a última).  

```blocks
let Pinha = game.createSprite(randint(0, 4), 0)
basic.forever(function () {
    if (Pinha.get(LedSpriteProperty.Y) == 4) {
        
    }
})
```

## {Pontuação}

Dentro do bloco de ``||logic:se||`` adicione o bloco ``||game:alterar pontuação em||``

```blocks
let Pinha = game.createSprite(randint(0, 4), 0)
basic.forever(function () {
    if (Pinha.get(LedSpriteProperty.Y) == 4) {
        game.addScore(1)
    }
})
```

## {Resetar a Pinha}

Para finalizar, precisamos fazer com que a ``||variables:Pinha||``, ao chegar na última linha, **volte para cima** novamente:
1. Dentro do segundo ``||logic:se||``, adicione um ``||basic:pausa 100(ms)||``.  
2. Use dois blocos ``||game:Pinha definir … para …||``.

- No primeiro, mude para **definir y para 0**.  

- No segundo, mude para **definir x** e coloque um ``||math:escolher aleatório 0 a 4||``.  

```blocks
let Pinha = game.createSprite(randint(0, 4), 0)
basic.forever(function () {
    if (Pinha.get(LedSpriteProperty.Y) == 4) {
        basic.pause(100)
        Pinha.set(LedSpriteProperty.Y, 0)
        Pinha.set(LedSpriteProperty.X, randint(0, 4))
    }
})
```

## {Finalizado}

Primeiro teste o jogo no preview do @boardname no lado esquerdo da tela.

Com o jogo finalizado e funcionando, conecte seu @boardname@ e clique em ``|Baixar|``.

Para aumentar a dificuldade basta diminuir a ``||basic:pausa||`` que fica logo no começo do sempre.
Divirta-se!

```template
basic.forever(function () { })
```
