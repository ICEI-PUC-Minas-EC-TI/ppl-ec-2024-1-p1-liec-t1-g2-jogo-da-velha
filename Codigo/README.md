<!-- LTeX: language=pt-BR -->

# Código do ESP32

Esse diretório contém todo o código do microcontrolador (SoC ESP32) escrito para
este projeto. A compilação pode ser feita no _Arduino IDE_, mas, por se tratar
de uma estrutura de código complexa, recomendamos o uso do
[PlatformIO Core](https://docs.platformio.org/en/latest/core/). O arquivo
[platformio.ini](platformio.ini) contém as configurações necessárias para
compilar e fazer o upload do código ao microcontrolador. Para fazer isso, basta
conectar o microcontrolador e executar (nesse diretório):

```bash
pio run -t upload
```

O código-fonte (mistura de C e C++), está em [src/](src), enquanto os arquivos
de cabeçalho estão em [include/](include). O arquivo
[.clang-format](.clang-format) define as regras de formatação do código-fonte, e
pode ser lido por alguns editores de código. Finalmente, o [Makefile](Makefile)
define um simples comando de compilação, para integrar o projeto às IDEs
compatíveis com [GNU Make](https://www.gnu.org/software/make/).