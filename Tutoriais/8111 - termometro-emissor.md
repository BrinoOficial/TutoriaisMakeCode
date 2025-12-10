# Termômetro sem fio com micro:bit – EMISSOR

## {Configurar o rádio}
Na categoria ``||radio:rádio||``, arraste **``||radio:definir grupo do rádio||``** para dentro do bloco ``||basic:no iniciar||``   e troque para **o número de grupo indicado pelo professor**.

```blocks
radio.setGroup(999)
```

## {Enviar leitura}
Dentro do bloco **``||basic:sempre||``** monte o código:
1. Pegue o bloco **``||radio:rádio envia número||``** e insira no bloco **``||basic:sempre||``** .  
2. Para enviar a temperatura pelo rádio insira o bloco``||input:temperatura (°C)||`` (``||input:Entrada||``) no bloco **``||radio:rádio envia número||``**.  
3. Adicione **``||basic:pausa (ms)||``** com **2000ms** (2 segundo) para que o programa aguarde um pouco antes de enviar a próxima leitura.

```blocks
basic.forever(function () {
    radio.sendNumber(input.temperature())
    basic.pause(2000)
})
```

## {Teste}
Baixe o código para o microbit emissor e siga as instruções no seu livro.
