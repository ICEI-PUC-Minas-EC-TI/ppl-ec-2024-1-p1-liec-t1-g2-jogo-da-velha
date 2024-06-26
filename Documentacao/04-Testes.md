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