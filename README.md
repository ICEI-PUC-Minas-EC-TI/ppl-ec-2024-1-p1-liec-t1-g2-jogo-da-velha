# Jogo da Velha Automático

`PUC Minas — Unidade Praça da Liberdade`

`Engenharia de Computação`

`2024/1 (1º Período)`

`Laboratório de Introdução à Engenharia de Computação`

## Integrantes

- Amanda Canizela Guimarães
- Antonella de Paula Menegaz
- Felipe de Faria Rios Coelho
- Lucas Alvarenga Fernandes
- Lucca Mendes Alves Pellegrini

## Orientador

- Felipe Augusto Lara Soares

## Resumo

![Apresentação do Projeto](Apresentacao/Figuras/apresentação_caixa.jpg)

Este repositório contém a apresentação, o código, e a documentação do projeto
“Jogo da Velha Automático”, desenvolvido no primeiro período do curso de
Engenharia de Computação da PUC Minas Praça da Liberdade. O projeto é
constituído por uma montagem (veja a figura acima) contando com uma matriz de
nove LEDs e dois botões, governados por um microcontrolador [DevKit
ESP32](https://www.espressif.com/en/products/socs/esp32). Trata-se de uma
implementação do [Jogo da Velha](https://pt.wikipedia.org/wiki/Jogo_da_velha),
opcionalmente controlada por um aplicativo de smartphone via Bluetooth ou por
um computador via USB.

O projeto conta com dois modos de jogo: jogador contra jogador, e jogador
contra computador. No primeiro desses, os jogadores definem entre si quem
jogará primeiro. Já no segundo modo, o usuário tem a opção de escolher quem vai
jogar primeiro, e de selecionar um de três níveis de dificuldade; isso pode ser
feito pelo aplicativo de smartphone, que conta com um placar para registrar a
pontuação, ou pelo computador, com uma conexão USB.

# [Código Fonte do Microcontrolador](Codigo/README.md)

O código fonte está [aqui](Codigo), e foi desenvolvido usando
[PlatformIO](https://platformio.org/).

# [Aplicativo para Smartphone](App/README.md)

O aplicativo está [aqui](App), e foi desenvolvido usando o [MIT App
Inventor](https://appinventor.mit.edu/).

# Apresentação

<ol>
<li><a href="Apresentacao/README.md"> Vídeo do Funcionamento</a></li>
<li><a href="Apresentacao/README.md"> Fotos do Projeto</a></li>
</ol>

# Manual de Utilização

<li><a href="Manual/manual de utilização.md"> Manual de Utilização</a></li>

# [Documentação](Documentacao/Documentação.pdf)

A documentação escrita contendo os detalhes e a cronologia do desenvolvimento
do projeto está [aqui](Documentacao/Documentação.pdf).
