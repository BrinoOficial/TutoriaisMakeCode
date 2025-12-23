# Energizando uma entrada

## Aprendendo a ligar e controlar um LED com o micro:bit @unplugged
![Imagem da Montagem](https://raw.githubusercontent.com/BrinoOficial/TutoriaisMakeCode/master/LEDMicrobit.png)

## {Energizando P0}
Primeiro, vamos acender o LED.

1. Com o circuito indicado no livro já montado, arraste de dentro da categoria `||pins:Pins|` o bloco `||pins:gravação digital pin (P0) para (0)||` para dentro de `||basic:no iniciar||`.
2. Atualize os valores para ligar a porta P0: `||pins:gravação digital pin (P0) para (1)||`

```blocks
pins.digitalWritePin(DigitalPin.P0, 1)
basic.forever(function () {
	
})

```

## {Teste}
Agora vamos testar o nosso circuito! Para isso conecte o microbit ao seu computador e , aperte em `||Baixar||` embaixo a esquerda.
Obs.: Caso o LED não acenda, verifique as conexões dos cabos.

## {Piscar o LED}
Agora vamos dar o próximo passo, vamos fazer o LED piscar. Para isso, apague o código anterior e faça o seguinte código no bloco `||basic:sempre||`.

Dentro de `||basic:sempre||`:
1. `||pins:gravação digital pin (P0) para (1)||`
2. `||basic:pausa 500(ms)||`
3. `||pins:gravação digital pin (P0) para (0)||`
4. `||basic:pausa 500(ms)||`

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(500)
})
```

## {Teste}
> Agora ao apertar em `||Baixar||`, o LED deve piscar.
> Ajuste a **pausa** para piscar mais rápido ou mais devagar.

## {Botão liga/desliga}
Agora iremos controlar o nosso LED com os nossos botões!

- A: Acende o LED
- B: Apaga o LED

Para isso, apague o código anterior. Vamos fazer um novo!


## {Criando o código}
1. Da categoria `||input:Entrada||` Arraste o bloco `||input:no botão (A) pressionado||` e dentro dele adicione o bloco `||pins:gravação digital pin (P0) para (1)||`.
2. Duplique o bloco `||input:no botão (A) pressionado||` e selecione o botão B, ficando `||input:no botão (B) pressionado||`. Dentro dele use `||pins:gravação digital pin (P0) para (0)||`.

```
blocks
input.onButtonPressed(Button.A, function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
})
input.onButtonPressed(Button.B, function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
})

```

## {Teste}
> Agora ao apertar em `||Baixar||` e teste os botões A e B para controlar o LED.

## {Desafio}
Vamos usar o que você aprendeu e tentar resolver alguns desafio!

1. **Economia inteligente:** faça o LED ligar com o botão e apagar sozinho após *10 s* ligado.
2. **Outras portas:** Tente controlar um LED em outra porta sem ser a 0.
3. **Mais luz:** Tente acender dois LEDs e controlar cada um deles.
4. **Casa inteligente:** Que sensores podemos asociar ao LED e ao Buzzer?

Obs.: Para ter acesso a todos os blocos de programação, **anote os desafios no livro** e conclua esse tutorial clicando em Feito!