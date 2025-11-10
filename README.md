# Monitor-De-Pastas
Programa em C criado em aula em 10/11/2025 que monitora uma pasta, detectando novos arquivos, modificações e exclusões, registrando todas as alterações no terminal e em um arquivo de log.


Para usar, primeiro crie uma pasta chamada teste no mesmo diretório do programa. Compile o código usando GCC com gcc monitor.c -o monitor e execute com ./monitor. Adicione, modifique ou remova arquivos na pasta teste e observe as alterações sendo registradas no terminal e no arquivo de log.

O código utiliza uma struct Arquivo para armazenar o nome e a data de modificação de cada arquivo. A função logar() escreve as mudanças no terminal e no arquivo de log, enquanto a função verificar() compara o estado atual da pasta com o estado anterior para detectar novas adições, modificações ou remoções. O main() inicia o monitoramento e executa o loop infinito de verificação a cada 5 segundos (configurável).

Exemplo de saída no terminal e log:

[2025-11-10 14:00:01] Monitor iniciado.
[2025-11-10 14:00:06] Novo arquivo: arquivo1.txt
[2025-11-10 14:00:11] Arquivo modificado: arquivo1.txt
[2025-11-10 14:00:16] Arquivo removido: arquivo2.txt

Autor: Higor Martins e Kauan Marchesini
