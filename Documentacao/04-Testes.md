<!-- LTeX: language=pt-BR -->

# Testes do Projeto

## Funcionamento dos LEDs

Inicialmente, fizemos uma montagem preliminar — já tendo escrito
[a primeira parte](03-Desenvolvimento.md#desenvolvimento-do-c%C3%B3digo) do
código — com apenas um dos LEDs conectados, para comprovar que podíamos
controlá-lo. Com o computador que tínhamos conosco, porém, não conseguimos fazer
o upload de nenhum programa para o microcontrolador, apesar de conseguir
compilá-lo normalmente. Testamos algumas ferramentes diferentes, como o _Arduino
IDE_, o _Visual Studio Code_ com plugins, e o _PlatformIO Core_, mas nenhuma
delas conseguiu fazer o upload do código. Como não tínhamos outro computador
disponível nesse momento, optamos por terminar a montagem com todos os LEDs,
supondo que estariam funcionando, e resolver esse problema depois.

Terminando a montagem do [primeiro protótipo](03-Desenvolvimento.md#montagem) e
usando outro computador, decidimos iniciar a programação das
[funções que controlam os LEDs](/Codigo/src/io.c). Para isso, seria necessário,
antes, finalmente comprovar que todos os LEDs estavam funcionando corretamente.
Ao tentar acender os LEDs, entretanto, notamos que que apenas alguns deles
estavam funcionando e, mesmo assim, estavam muito fracos. Após muitas horas
testando, foi só quando verificamos as tensões nos circuitos com um multímetro,
notando que não existia a diferença de potencial esperada entre o pino de 5V e o
_ground_, que percebemos o problema: a referência que usamos para a pinagem,
mostrada abaixo, era para outro modelo de DevKit ESP32.

![Pinagem incorreta que usamos](Figuras/pinout_errado.png)

Cometemos esse erro porque o DevKit que compramos é uma placa mais estreita que,
portanto, não tem espaço para a legenda nos pinos, então não é possível saber a
numeração de cada pino sem consultar a referência. Quando encontramos a
documentação oficial do fabricante, descobrimos que deveríamos usar a mesma
pinagem dos DevKits oficiais da Espressif, empresa que desenvolveu a plataforma,
mostrada abaixo. Desconectando e reconectando todos os jumpers macho-macho de
acordo, o problema foi corrigido, e comprovamos que todos os LEDs estavam
funcionando como esperado.

![Pinagem correta para a correção](Figuras/pinout_correto.png)

## Implementação do jogo

Com a montagem corrigida, testamos também se o display na matriz de LEDs estava
corretamente ordenado, se o microcontrolador era capaz de jogar nas três
dificuldades, e se o sistema era capaz de corretamente detectar vitória, empate,
e jogadas inválidas, e reagir apropriadamente. Para isso, usamos a função de
[debugging pela porta serial](/Manual/README.md#debugging), executando vários
jogos em cada modo de jogo e em cada dificuldade, e comprovamos que tudo estava
funcionando como esperado.

## Instalação dos botões

Tendo corrigido os problemas acima, terminamos o
[código de controle](/Codigo/src/io.c) e decidimos fazer a instalação dos
botões. Originalmente, planejávamos usar seis ou mais botões de controle, com um
botão para selecionar cada linha, e outro para selecionar cada coluna, e
implementar assim a seleção das coordenadas de uma jogada. Após testar algumas
implementações possíveis, percebemos que nem todos os pinos GPIO do DevKit
poderiam ser usados para ler a entrada dos botões. Consultando a documentação da
plataforma, descobrimos alguns detalhes sobre a plataforma que frustraram nosso
plano original:

- Os pinos **6 a 11** do DevKit são conectados diretamente à memória flash do
  módulo ESP32. Portanto, não devem ser usados como pinos GPIO normais.
- Os pinos **0, 2, 12 e 15**, se usados como pinos de entrada, servem funções
  especiais durante a inicialização do módulo e, dependendo do seu estado
  (`HIGH` ou `LOW`), podem ter efeitos inesperados.
- Os pinos **34 a 39**, que são somente de entrada, foram os que havíamos
  considerado usar para conectar os seis botões. Entretanto, os pinos 37 e 38
  não são expostos como GPIO nesse DevKit, e os pinos restantes não seriam
  suficientes para conectar seis botões.

Com esse restultado e essas considerações, decidimos repensar a forma como o
jogo seria controlado, e decidimos usar apenas dois botões: um para mover um
_cursor_ sobre cada jogada possível, e outro para confirmar a seleção.
Conectando os dois botões e comprovando que funcionavam, terminamos a maior
parte do código, faltando apenas implementar a conexão Bluetooth quando o
aplicativo estivesse pronto.

## Funcionamento do aplicativo

Após implementar um protótipo da interface do aplicativo, usando diferentes
_telas_ no _App Invetor_ para cada menu, começamos a escrever
[o código em blocos](03-Desenvolvimento.md#c%C3%B3digo) mas, quando testamos o
cliente Bluetooth, percebemos que não era possível enviar nem receber mensagens
ao microcontrolador, exceto no menu principal. Ao investigar a documentação do
_App Inventor_, descobrimos que os eventos de elementos no layout de uma tela
não podem ser acessados no código de outra tela e, como o cliente Bluetooth é um
elemento de layout, ele está fora de escopo nas outras telas. Para consertar
isso, foi necessário refatorar a estrutura do aplicativo, implementando os
diferemtes menus como “pseudo-telas”, que na verdade são arranjos verticais.
Para mudar de um menu para o outro, implementamos procedimentos que tornariam
cada arranjo visível ou invisível, conforme necessário. Assim, o cliente
Bluetooth está sempre em escopo, e o problema é resolvido.