# Manual de Utilização

## Como ligar o dispositivo

Para ligar o dispositivo, remova a tampa da caixa tomando cuidado para não
desconectar nenhum dos fios dentro. Retire o cabo USB incluído, e o conecte à
entrada microUSB do microcontrolador ESP32, certificando-se de passar o cabo
pelo furo na lateral da tampa. Tendo-lo conectado, retorne a tampa à caixa,
alinhando o corte na lateral com o furo do cabo USB. Finalmente, conecte a
outra extremidade do cabo a uma fonte de energia. Tome a primeira demonstração
[aqui](/Apresentacao/README.md#setup-inicial-e-jogo-nas-configura%C3%A7%C3%B5es-padr%C3%A3o)
como exemplo.

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

## Configuração

Para definir as configurações do jogo, é necessário parear o dispositivo a um
smartphone usando Bluetooth, e fazer as configurações no
[aplicativo](../App/README.md). Para isso, deve-se manter o botão esquerdo
pressionado ao ligar o dispositivo — se o botão estiver pressionado no término
da animação inicial, todos os LEDs piscarão duas vezes na a cor verde, e o
dispositivo estará pronto para parear, o que se faz no menu de configurações
Bluetooth do sistema. O nome da interface Bluetooth do dispositivo será “O Jogo
da Velha”.

Quando o sistema estiver pareado ao dispositivo, abra o aplicativo e selecione o
botão “Conectar” no menu inicial. Isso abrirá uma lista de todos os dispositivos
pareados; selecione “O Jogo da Velha”. Se a conexão for estabeleida, você verá o
texto “Dispositivo conectado” abaixo do botão.

A partir desse ponto, já é possível iniciar o jogo com as configurações
desejadas: basta escolher o modo de jogo na tela inicial (_singleplayer_ ou
_multiplayer_) e, se esolher _singleplayer_, a dificuldade do jogo e quem jogará
primeiro. Enquanto uma partida não for iniciada, os LEDs da matriz permanecerão
piscando em um loop. Quando for iniciada, um placar aparecerá na tela do
aplicativo, contando as vitórias de cada oponente.

A qualquer momento, é possível retornar ao menu principal ao selecionar o botão
“Voltar ao Menu Principal”, na parte inferior da tela. Lá, também será possível
voltar ao jogo, se um estiver em progresso, ao apertar o botão “Voltar ao Jogo”.
Note, porém, que, ao selecionar “Singleplayer” ou “Multiplayer” no menu inicial,
o jogo atual será interrompido e o placar será zerado. Finalmente, caso o
aplicativo perca a conexão ao dispositivo, pode-se voltar ao menu inicial para
reestabelecer a conexão e voltar ao jogo, mas não há garantia que o placar
continuará sincronizado. Veja a segunda demonstração
[aqui](/Apresentacao/README.md#setup-bluetooth-jogo-dif%C3%ADcil-e-jogo-multiplayer).


# Uso Avançado

## Debugging

É possível, ao invés de usar Bluetooth, fazer a configuração do dispositivo com
uma conexão serial, ao conectar o cabo USB ao computador e, ao terminar a
animação inicial, manter pressionado o botão direito. Isso exibirá indicadores
semelhantes aos do modo Bluetooth, descrito acima, mas com LEDs vermelhos. O
dispositivo ficará ocioso, piscando os LEDs, até que receba uma entrada pela
porta serial. Quando isso acontecer, as opções de configuração do aplicativo
serão disponibilizadas na linha de comando do monitor serial, exceto que é
introduzido um novo modo de jogo, computador vs. computador (_no-player_),
sendo possível escolher a dificuldade de cada um independentemente.

Essa função só deve ser usada para debugging, pois não conta com a interface de
jogo do aplicativo, e, ao final de cada partida, não iniciará a próxima
automáticamente, sendo necessário reconfigurar o jogo cada vez. Para facilitar
o debugging, entretanto, um desenho em ASCII do tabuleiro será exibido antes e
depois de cada jogada.
