# Termômetro sem fio com micro:bit – RECEPTOR

## {Configurar o rádio}
Na categoria ``||radio:rádio||``, arraste **``||radio:definir grupo do rádio||``** para dentro do bloco ``||basic:no iniciar||``   e troque para **o número de grupo indicado pelo professor**.

```blocks
radio.setGroup(999)
```

## {Mostrar leitura}
1. Pegue o bloco **``||radio:ao receber rádio:receivedNumber||``** e insira no seu código.  
2. Para mostrar a temperatura recebida insira o bloco ``||basic:mostrar número||`` (``||basic:Básico||``) dentro do bloco **``||radio:ao receber rádio:receivedNumber||``**.
3. Altere o valor a ser mostrado no bloco ``||basic:mostrar número||`` (``||basic:Básico||``) pela variável ``||variables:receivedNumber||`` 

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    basic.showNumber(receivedNumber)
})
```

## {Colocando o código no micro:bit}

Conecte o @boardname@ no computador, clique no botão ``|Download|`` e siga os passos para baixar o código para a sua placa.

⭐ Ótimo trabalho! ⭐ Você transformou o micro:bit no Termômetro sem fio com micro:bit – RECEPTOR

Ao ligar o emissor, os números devem aparecer no display do micro:bit.
