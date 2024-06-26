# Conclusão

Em suma, o jogo da velha foi desenvolvido com sucesso, apesar das complicações
que discutimos. O código do microcontrolador e o aplicativo foram as partes mais
trabalhosas, e demoraram muito mais do que originalmente esperávamos. Vários
usuários já testaram os diferentes modos de jogo e dificuldades, e não
encontramos mais problemas. A respeito do que poderia ser melhorado, algumas
sugestões que recebemos são deixadas para possíveis versões futuras:

- **Alternação de jogadores**: implementar a opção configurável de alternar qual
  dos dois jogadores terá a primeira jogada em cada partida.
- **Implementação de variantes do jogo**: como, por exemplo:
  - **Jogo da Velha com Quatro peças**: nesta variante, cada jogador só pode ter
    quatro de suas peças, _X_ ou _O_, no tabuleiro de cada vez. Para fazer outra
    jogada, é necessário antes remover uma das que já foram colocadas.
  - _**Wild Tic-tac-toe**_: em que cada jogador pode escolher qual peça vai
    colocar na sua jogada, _X_ ou _O_.
  - **Jogo da Velha Misère**: em que o jogador que alinhar três de suas peças
    perde.
  - **Notakto**: semelhante ao anterior, mas em que ambos os jogadores jogam com
    as mesmas peças.
- **Mais níveis de dificuldade**: especialmente um nível de dificuldade entre o
  normal e o difícil, possivelmente implementando o minimax com uma
  probabilidade configurável de ignorar a melhor jogada.
- **Persistência do placar**: fazendo com que o placar possa ser salvo e
  recarregado quando fechamos e abrimos novamente o aplicativo.
- **Menu de recordes**: tal que, ao terminar um número de partidas, um jogador
  possa entrar seu nome no aplicativo e salvar a sua pontuação (razão entre
  vitórias e derrotas) em um placar persistente de recordes.
- **Controle pelo aplicativo**: possibilitando jogar sem ter que usar os botões
  físicos na montagem, possivelmente habilitando jogos entre dois jogadores em
  que um jogador usa a montagem, enquanto o outro usa o smartphone.
- **Multiplayer via WiFi/Bluetooth**: em que duas montagens iguais possam se
  comunicar com um protocolo simples, e, assim, permitir jogos Multiplayer em
  que cada jogador tem o seu próprio dispositivo.