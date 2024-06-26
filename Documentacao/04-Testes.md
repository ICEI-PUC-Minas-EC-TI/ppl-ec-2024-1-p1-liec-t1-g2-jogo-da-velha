# Testes do Projeto

## Funcionamento dos LEDs

Quando terminamos a montagem do
[primeiro protótipo](03-Desenvolvimento.md#montagem), decidimos iniciar a
programação das funções [que controlam os LEDs](/Codigo/src/io.c). Para isso,
foi necessário antes testar se todos os LEDs estavam funcionando corretamente.
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