# Metodologia

## Divisão de Papéis

A equipe usou a framework _Scrum_ como base para gerenciar o desenvolvimento
ágil do projeto, assim dividindo as tarefas entre os membros da equipe,
organizada da seguinte maneira:

- **Product Owner**: Amanda Canizela;
- **Scrum Master**: Lucca Pellegrini;
- **Equipe de Desenvolvimento:** Amanda Canizela, Antonella Menegaz, Felipe
  Rios, Lucas Alvarenga, Lucca Pellegrini.

## Processo

1. A equipe se reuniu e definiu a estrutura geral do projeto, incluindo os
   diferentes modos de jogo e dificuldades disponíveis, as funções e a interface
   do aplicativo, e a estrutura física do tabuleiro, com o emprego de uma matriz
   de nove LEDs RGB e de 6 a 10 botões para configuração e controle.
2. A divisão dos papéis foi feita pela Amanda e pela Antonella, em consulta com
   o resto do grupo, assim:
   - **Amanda**: Distribuição das tarefas, escrita da documentação, e montagem
     do projeto.
   - **Antonella**: Definição, organização e distribuição das tarefas, e
     organização e escrita da documentação.
   - **Felipe**: Design e programação do aplicativo, e manuntenção do
     repositório do projeto.
   - **Lucas**: Orçamento e aquisição dos materiais, e design e montagem do
     projeto.
   - **Lucca**: Organização do código, programação do ESP32, design, montagem e
     acabamento do projeto, e administração do repositório do projeto.
3. As tarefas foram organizadas no [_Trello_](https://trello.com/pt-BR) pela
   Amanda e pela Antonella.
4. Com as tarefas divididas e organizadas, iniciamos o desenvolvimento, que está
   documentado em detalhes [aqui](03-Desenvolvimento.md).

![Imagem do quadro kanban no Trello enquanto terminávamos o
  projeto](Figuras/kanban.jpeg)

## Ferramentas

As ferramentas utilizadas no projeto foram:

- **Organização e divisão de tarefas**: [Trello](https://trello.com/pt-BR).
- **Design e desenvolvimento do aplicativo**:
  [MIT _App Inventor_](https://appinventor.mit.edu/).
- **Programação do microcontrolador**:

  - **Edição do código**: Inicialmente,
    [Arduino IDE](https://docs.arduino.cc/software/ide/) e
    [Visual Studio Code](https://code.visualstudio.com/). Depois, para maior
    flexibilidade e performance, [NeoVim](https://neovim.io/) com
    [clangd](https://clangd.llvm.org/features) e
    [clang-format](https://clang.llvm.org/docs/ClangFormat.html).
  - **Compilação e debugging**:
    [PlatformIO Core](https://docs.platformio.org/en/latest/core/) e
    [GNU Make](https://www.gnu.org/software/make/).

- **Escrita da documentação**: [Office 365](https://www.office.com/) e, na
  revisão, [NeoVim](https://neovim.io/) com
  [LTeX](https://valentjn.github.io/ltex/) e [Prettier](https://prettier.io/).