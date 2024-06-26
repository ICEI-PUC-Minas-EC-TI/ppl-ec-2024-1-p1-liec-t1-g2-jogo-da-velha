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

Como descrevemos [na discussão dos testes](04-Testes.md), não foi possível
implementar as telas do aplicativo como telas próprias do _App Inventor_. Por
isso foram representadas como `VerticalArrangement`, e a a mudança entre as
telas é feita tornando cada arranjo visível ou invisível. Para cada botão, foi
adicionado um bloco determinando qual mudança de tela será feita, e qual código
numérico será enviado ao microcontrolador via Bluetooth quando for pressionado.

Adicionamos, também, blocos determinando que, ao selecionar o botão “Conectar”,
os elementos da lista de seleção serão iguais aos endereços e nomes dos
dispositivos detectados pelo cliente Bluetooth. Ao efetivar, nela, a escolha do
microcontrolador, um outro bloco executa, realizando a conexão, e mostrando na
tela uma mensagem indicando se a conexão teve êxito ou não. Finalmente, um bloco
_Timer_ verifica constantemente se algum código foi recebido do microcontrolador
via Bluetooth e, se for o caso, guarda o código em uma variável global e,
dependendo de qual for, realiza procedimento apropriado.

![Código do aplicativo em blocos](Figuras/blocos.png)

## Desenvolvimento do Hardware

### Montagem

O primeiro protótipo consistiu de nove LEDs RGB conectados à protoboard com
ternos de jumpers de conectores macho-fêmea, deixando o pino do diodo azul
desconectado, pois ele não é necessário. Para o _ground_ de cada LED,
conectamo-lo por meio de um resistor à linha negativa da protoboard, e para cada
pino dos diodos verde e vermelhos, conectamo-lo a uma das portas GPIO do
microcontrolador por meio de jumpers macho-macho. Isso exigiu um número maior de
jumpers, mas constituiu uma montagem marginalmente mais organizada. Veja o
protótipo abaixo:

![Primeiro protótipo](Figuras/prototipo.jpg)

Deivido à instabilidade da conexão, usamos fita isolante para prender os pinos
dos LEDs aos conectores fêmea dos jumpers e garantir que será sempre possível
fechar o circuito. Como descrito [na seção de testes](04-Testes.md), esse
protótipo teve que ser desmontado e refeito. Quando foi comprovado que todos os
LEDs estavam funcionando e corretamente mapeados no código, adicionamos os Push
Buttons, usando o mesmo padrão de jumpers macho-fêmea, macho-macho, e
resistores. Uma vez instalados, terminamos e testamos extensivamente o código do
microcontrolador — com exceção da implementação do Bluetooth — e instalamos a
montagem na caixa.

Inicialmente, haviamos considerado colar as protoboards (pois não sabíamos se
apenas uma seria suficiente), usando a fita dupla-face que elas incluem, às
laterais da parte interna da caixa, mas logo percebemos que seria mais fácil
utilizar e fazer a manutenção do projeto se a montagem inteira fosse colada à
parte interna da tampa. Isso faria com que fosse conveniente abrir a caixa,
tanto para fazer manutenção quanto para guardar o manual impresso e o cabo
Micro-USB, quando não estiver em uso. Após tomar as medidas da tampa e dos
componentes e comprovar que seria possível, decidimos fazer isso.

Com lápis e esquadro, então, determinamos as posições da protoboard, de cada
LED, e dos dois botões com marcações no interior da tampa. Usando uma furadeira,
fizemos furos de 5mm de diâmetro para cada LED — fazendo com que se encaixassem
com firmeza e facilidade — e quatro furos de tamanho semelhante para os
conectores fêmea dos jumpers dos botões, firmando os conectores com cola quente
no lado interno. Além disso, fizemos um furo com diâmetro de aproximadamente
15mm na lateral da tampa, para a saída do cabo adaptador Micro-USB, e um corte
correspondente na caixa, para que seja possível tampá-la e destampá-la sem
desconectar o cabo.

Com todos os furos feitos, instalamos primeiro os botões, fixando-os com cola
quente e Super Bonder aos conectores. Depois, colamos a protoboard usando fita
dupla-face, conectando os jumpers dos botões a ela novamente, e, finalmente,
encaixamos os LEDs nos furos de 5mm e os fixando com Super Bonder. A montagem
final pode ser vista abaixo:

![Instalação da montagem na tampa da caixa](Figuras/instalação_na_caixa.jpg)
![Montagem terminada](Figuras/caixa_completa.jpg)

### Desenvolvimento do Código

O desenvolvimento do código do microcontrolador foi dividido em duas partes: a
implementação interna da lógica do jogo, e a implementação dos aspectos
relacionados ao hardware, como controle de LEDs, leitura de botões, conexão
serial via USB e Bluetooth, etc.

A primeira parte pode ser resumida assim:

- Implementação de funções básicas de jogo:
  ```c
  bool check_draw(char board[SIZE][SIZE]);
  bool check_win(char board[SIZE][SIZE], char player);
  bool make_move(char board[SIZE][SIZE], int row, int col, char player);
  void init_board(char board[SIZE][SIZE]);
  void print_board(char board[SIZE][SIZE]);
  ```
- Implementação do jogador controlado pelo microcontrolador:
  ```c
  void cpu_move(char board[SIZE][SIZE], char player, Difficulty difficulty);
  static void medium_move(char board[SIZE][SIZE], char player);
  static void hard_move(char board[SIZE][SIZE], char player);
  static int minimax(char board[SIZE][SIZE], bool is_maximizing, char player,
         char opponent);
  ```

E a segunda parte, resumidamente, assim:

- Definição dos pinos GPIO e definições de cores dos LEDs:

  ```c
  #define BTN1 34
  #define BTN2 35
  #define NUM_LEDS 9

  static const int reds[NUM_LEDS] = { 15, 0, 16, 5, 19, 22, 13, 14, 26 };
  static const int greens[NUM_LEDS] = { 2, 4, 17, 18, 33, 23, 12, 27, 25 };

  typedef enum {
    BLANK,
    RED,
    GREEN
  } Color;
  ```

- Definição das funções de controle da matriz de LED, incluindo a implementação
  do controle de um cursor:

  ```c
  // Função para definir a cor de um LED específico.
  void set_led_color(int led_pos, Color color);
  // Função para exibir o tabuleiro inteiro na matriz de LEDs.
  void print_led_board(char board[SIZE][SIZE]);
  // Função para detectar o estado do botão.
  bool is_button_pressed(int button_pin);
  // Função para mover o cursor para a próxima posição vazia.
  void move_cursor(int *cursor_pos, char board[SIZE][SIZE]);
  // Função para piscar o LED na posição do cursor.
  void flash_cursor(int cursor_pos, char player);
  ```

- Implementação das várias animações exibidas na matriz de LEDs.
- Definição das funções de configuração de jogo, com exceção da configuração
  pelo aplicativo via bluetooth:

  ```c
  typedef struct {
    bool is_set;
    int game_mode;
    Difficulty difficulty;
    enum { PLAYER, CPU } first;
  } Options;

  typedef enum {
    DEFAULT_SETTINGS,
    SERIAL_SETTINGS,
    BLUETOOTH_SETTINGS
  } SettingsMode;
  ```

  ```c
  static SettingsMode SM;

  // Função para determinar de onde as configurações serão lidas.
  void set_sm(void);
  // Função de setup inicial, que depende de onde as configurações serão lidas.
  void modal_setup(void);
  // Função que lê as configurações de jogo pela porta serial.
  static void get_serial_settings(Options *opt);
  // Função pública (exportada) para abstrair a leitura de configurações.
  void get_settings(Options *opt);
  ```

- Implementação da comuinicação via Bluetooth:

  ```c
  typedef enum {
    // Tela de seleção de modo de jogo.
    PVP = 1,
    PVE = 2,

    // Tela de seleção de dificuldade.
    EASY_DIFF = 3,
    NORMAL_DIFF = 4,
    HARD_DIFF = 5,

    // Tela de escolha de quem vai jogar primeiro.
    PLAYER_FIRST = 6,
    CPU_FIRST = 7,

    // Tela de jogo.
    SCORE_P1 = 8,
    SCORE_P2 = 9,
  } BtMsg;

  typedef enum { CONTINUE, RETURN } BtAction;
  ```

  ```c
  static Options SettingsBT = { .is_set = false };
  static BluetoothSerial SerialBT;

  // Função que lê as configurações de jogo enviadas pelo aplicativo.
  static void get_bt_settings(Options *opt);
  /* Função usada para verificar se há mensagem Bluetooth recebida enquanto um
   * jogo está em progresso e, se for o caso, interromper o jogo atual. */
  BtAction check_and_handle_bt(void);
  ```

## Comunicação entre App e Hardware

Como indicado acima, a comunicação entre o aplicativo e o microcontrolador foi
implementada por meio da definição de nove códigos numéricos de oito bits.
Originalmente, foi considerado definir cada código como uma potência de dois,
para que fosse possível enviar vários comandos em uma única mensagem de um ou
mais bytes, usando operações booleanas binárias, como
`SerialBT.write(MSG_1 | MSG_2 | MSG_3);`, mas, devido ao aumento da complexidade
que seria necessário no código em blocos do _App Inventor_, essa ideia foi
descartada. Dos nove comandos, sete são enviados pelo aplicativo, enquanto os
outros dois são enviados pelo microcontrolador. Em ordem numérica de 1 a 9, eles
são:

- `PVP` e `PVE`: indicam, respectivamente, que o usuário escolheu jogar contra
  outro jogador ou contra o computador.
- `EASY_DIFF`, `NORMAL_DIFF` e `HARD_DIFF`: determinam, respectivamente, que o
  usuário selecionou a dificuldade fácil, normal, ou difícil.
- `PLAYER_FIRST` e `CPU_FIRST`: definem, num jogo contra o computador,
  respectivamente, que o usuário selecionou que o usuário vai jogar primeiro, ou
  que o computador vai jogar primeiro.
- `SCORE_P1` e `SCORE_P2`: são as únicas mensagens enviadas pelo
  microcontrolador, indicando, respectivamente, que o primeiro jogador ganhou
  partida, ou que o segundo jogador (ou o computador) ganhou uma partida.