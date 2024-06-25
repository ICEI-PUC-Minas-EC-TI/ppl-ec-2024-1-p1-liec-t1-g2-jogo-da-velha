# Desenvolvimento

## Materiais

Os materiais utilizados no projeto foram:

- Um microcontrolador
  [DevKit ESP32 (KS0413)](https://github.com/keyestudio/KS0413-Keyestudio-ESP32-Core-Board-_Black-and-Eco-friendly/blob/master/KS0413.md).
- Uma protoboard de 830 pontos.
- Uma caixa de papelão de alta qualidade.
- Nove LEDs RGB (cátodo comum).
- Dois Push Buttons 12x12mm com capa amarela.
- 11 resistores de 1kΩ.
- 31 jumpers com conectores macho-fêmea.
- 22 jumpers com conectores macho-macho.
- Um cabo adaptador USB-A para Micro-USB.
- Cola quente e Super Bonder.

## Desenvolvimento do Aplicativo

### Interface

A interface foi desenvolvida de forma simples, com poucas telas para a
configuração do jogo, e uma tela para acompanhar o jogo com um placar de
vitórias. Tendo dividido assim as telas, determinou-se o layout dos elementos:

- **Menu Principal**: sendo a primeira tela, adicionou-se um botão para
  selecionar cada modo de jogo, Singleplayer e Multiplayer, e um botão
  “Conectar” para estabelecer a conexão Bluetooth entre o aplicativo e o
  microcontrolador. Além desses, adicionamos um botão de “Voltar ao jogo”, que
  só é visível quando uma partida já está em progresso.
- **Escolha de Dificuldade**: ao escolher o modo Singleplayer, a segunda tela
  apresenta quatro botões, três dos quais são usados para selecionar a
  dificuldade do jogo: fácil, normal, ou difícil. Também incluímos um botão de
  “Voltar ao menu principal”, para cancelar a escolha.
- **Escolha de Jogador**: ao escolher a dificuldade, a terceira tela apresenta
  dois botões, um dos quais fará o computador jogar primeiro, enquanto o outro
  fará com que o usuário jogue primeiro. O mesmo botão de “Voltar ao menu
  principal” foi incluido, e, aqui, também cancela a configuração do jogo.
- **Tela de Jogo**: finalmente, a tela de jogo aparece quando a primeira partida
  se inicia. Ela conta com um placar de dois números, incialmente zero, para o
  primeiro e o segundo jogador (em caso de jogo Multiplayer), ou para o jogador
  e o computador (em caso de jogo Singleplayer). O botão de “Voltar ao menu
  principal” está aqui também mas, nesse caso, pressioná-lo não cancelará o
  jogo, pois no menu principal será possível selecionar o botão “Voltar ao
  jogo”. Portanto, o menu principal passa a funcionar como um menu de _pause_.

### Código

![Código do aplicativo em blocos](Figuras/blocos.png)

Descreva o desenvolvimento do código do aplicativo.

## Desenvolvimento do Hardware

### Montagem

Descreva como foi o processo da montagem do projeto.

### Desenvolvimento do Código

Descreva como foi o desenvolvimento do código do arduino/ESP.

## Comunicação entre App e Hardware

Descreva como foi o processo de comunicação entre App e arduino/ESP.