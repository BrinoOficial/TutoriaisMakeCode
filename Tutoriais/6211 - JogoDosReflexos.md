# Jogo dos Reflexos

## Sobre o jogo
O jogo dos reflexos é um jogo em que o jogador deve clicar no botão A no exato momento que um ponto (sprite) passar pelo centro da tela.

Obs.: O termo sprite vem do inglês e é comumente utilizado para se referir a uma imagem ou objeto 2D.

## {Criando nosso sprite}
1. Na categoria ``||variables:Variáveis||``, clique em **"Fazer uma variável..."** e chame-a de ``||variables:sprite||``.
2. Arraste o bloco ``||variables:definir sprite para(0)||`` (``||variables:Variáveis||``) para dentro do bloco ``||basic:no iniciar||``.
3. Na categoria ``||game:Jogo||`` (Avançado), pegue o bloco ``||game:criar sprite em x: (2) y:(2) ||`` e coloque-o dentro do bloco ``||variables:definir sprite para(0)||`` substituindo o **0**. 

```blocks
let sprite = game.createSprite(2, 2)
```

## {Movendo nosso sprite}
O nosso sprite começa no nosso jogo no meio, virado para o lado direito. 
Para movê-lo acesse a categoria ``||game:Jogo||`` e utiliza o bloco ``||game:(sprite) mover por (1)||`` dentro de ``||basic:sempre||``. 
Assim nosso ``||variables:sprite||`` se moverá para a direita.

```blocks
let sprite = game.createSprite(2, 2)
basic.forever(function () {
    sprite.move(1)
})
```

## {Quicando nas paredes}
Para que o nosso sprite quique de um lado para o outro, siga os passos dentro do bloco ``||basic:sempre||``:
1. Na categoria ``||game:Jogo||``, use o bloco ``||game:(sprite)se na borda, saltar||`` para fazer o ``||variables:sprite||`` quicar na borda da tela. 
2. Também adicione um bloco ``||basic:pausa (ms) (100)||`` para que ele não se mova muito rápido.

```blocks
let sprite = game.createSprite(2, 2)
basic.forever(function () {
    sprite.move(1)
    sprite.ifOnEdgeBounce()
    basic.pause(100)
})
```

## {Configurando o botão}
Para testar nossos reflexos, vamos criar um código que quando **A** for pressionado, testa se o ``||variables:sprite||`` está no centro ou não:
1. Na categoria ``||input:Entrada||`` adicione o bloco``||input:no botão A pressionado||`` ao nosso código. 
2. Da categoria ``||logic:Lógica||``, arraste o bloco ``||logic:se ... senão||`` para dentro dele.

```blocks
let sprite = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    if (true) {
    } else {
    }
})
```

## {Construindo a lógica}
Agora iremos construir a lógica do nosso bloco ``||logic:se ... senão||``! O nosso objetivo é saber se o nosso sprite está no meio, para isso, devemos conferir qual a posição atual do nosso sprite no eixo X:
1. Na categoria ``||logic:Lógica||`` arraste o bloco  ``||logic:(0) = (0)||`` para dentro da condição do ``||logic:se||``
2. Da categoria ``||game:Jogo||``, utilize o bloco ``||game:sprite x||`` no primeiro espaço do ``||logic:=||``
3. No segundo espaço de ``||logic:=||`` iremos colocar o número **2**, que é o endereço (index) do LED central da nossa matriz de LEDs

```blocks
let sprite = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    if (sprite.get(LedSpriteProperty.X) == 2) {
    } else {
    }
})
```

## {Pontuação}
Agora que criamos a lógica de comparação do nosso jogo está na hora de adicionar um contador de pontuação! Para isso siga os passos para preencher o nosso bloco de ``||logic:se ... senão||``:
1. No ``||logic:se||`` do bloco ``||logic:se ... senão||``! vamos adicionar o bloco ``||game:alterar pontuação||`` da categoria ``||game:Jogo||``
2. Já no ``||logic:senão||`` devemos ter o bloco ``||game:fim de jogo||`` da categoria ``||game:Jogo||`` 

```blocks
let sprite = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    if (sprite.get(LedSpriteProperty.X) == 2) {
        game.addScore(1)
    } else {
        game.gameOver()
    }
})
basic.forever(function () {
    sprite.move(1)
    basic.pause(100)
    sprite.ifOnEdgeBounce()
})
```

## {Testando reflexos}
Chegou a grande hora! Vamos testar o nosso jogo dos reflexos. Primeiro teste o jogo no preview do micro:bit no lado esquerdo da tela.

Com o jogo finalizado e funcionando, conecte seu micro:bit, clique em ``|Baixar|`` e siga os passos apresentados.

Divirta-se e melhore o seu jogo!
