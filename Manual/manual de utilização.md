# Manual de Utilização

## Como ligar o dispositivo

Para ligar o dispositivo, remova a tampa da caixa tomando cuidado para não
desconectar nenhum dos fios dentro. Retire o cabo USB incluído, e o conecte à
entrada microUSB do microcontrolador ESP32, certificando-se de passar o cabo
pelo furo na lateral da tampa. Tendo-lo conectado, retorne a tampa à caixa,
alinhando o corte na lateral com o furo do cabo USB. Finalmente, conecte a
outra extremidade do cabo a uma fonte de energia. Tome a demonstração
[aqui](Apresentacao/Vídeos/demo_setup.webm) como exemplo.

Feito isso, o dispositivo irá ligar e, a menos que o usuário aperte algum
botão, um jogo começará com as configurações padrão. Para desligar, desconecte
o cabo da fonte de energia — não há risco de dano ao dispositivo por
desconectá-lo enquanto joga.


## Como jogar

Quando o dispositivo liga, ele exibe uma curta animação na matriz de LEDs,
tanto para comprovar o funcionamento de ambas as cores de todos os LEDs quanto
para indicar a conclusão do *setup* inicial. Se nenhum dos botões estiver
pressionado quando a animação acabar, um jogo será iniciado com as
configurações padrão. Isso é, o usuário jogará primeiro, contra o computador,
na dificuldade normal.

### Controles

Ao começo de cada partida, o primeiro LED começará a piscar; isso indica a
posição do cursor. A cor do cursor indica de quem é a jogada: em um jogo contra
o computador, verde corresponde ao jogador humano, e vermelho corresponde ao
computador; enquanto, em um jogo entre dois jogadores, verde corresponde ao
primeiro jogador, e vermelho corresponde ao segundo.

Para mover o cursor, pressione o botão esquerdo (pode ser necessário mantê-lo
pressionado por até 500ms para que seja detectado), e o cursor moverá para a
próxima casa vazia. Pode-se manter o botão pressionado constantemente, para
iterar sobre as casas vazias mais rápido. Para confirmar sua seleção, pressione
o botão direito. Ao final da partida, uma animação indicará o jogador vitorioso
ou, em caso de empate, indicará isso, piscando brevemente todos os LEDs. A
próxima partida será iniciada automaticamente.
