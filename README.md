# Monitor de Pastas em C  
**Autores:** Kauan Perine Marchesini e Higor Martins

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

## 1. Resumo do Projeto
O programa monitora continuamente uma pasta e identifica três tipos de eventos:
- Arquivos novos  
- Arquivos modificados  
- Arquivos removidos  

Todas as alterações são registradas no arquivo `monitor.log` e exibidas na tela.

---

## 2. Funcionamento do Código

1. Bibliotecas Importadas
O código usa bibliotecas para:
	•	Entrada/saída (stdio.h)
	•	Manipulação de strings (string.h)
	•	Leitura de diretórios (dirent.h)
	•	Informações de arquivos (sys/stat.h)
	•	Pausa de execução (unistd.h)
	•	Controle de tempo (time.h)
  
2. Definições (Macros)
#define PASTA "./teste"
#define LOG "monitor.log"
#define INTERVALO 5
Essas constantes definem:
	•	A pasta monitorada
	•	O arquivo de log
	•	O intervalo de tempo entre verificações

3. Estrutura Arquivo
typedef struct {
    char nome[256];
    time_t mod;
} Arquivo;
Representa cada arquivo da pasta com:
	•	Nome
	•	Data da última modificação

4. Função listar()
Responsável por:
	•	Abrir a pasta
	•	Percorrer todos os arquivos
	•	Coletar nome e horário de modificação
	•	Preencher um vetor de Arquivo
Retorna 1 se conseguiu listar, 0 se falhou.

5. Função logar()
Registra eventos:
	•	Imprime na tela
	•	Escreve no arquivo monitor.log
	•	Inclui timestamp (data e hora atual)

6. Função main()
Onde acontece o monitoramento.

a) Declara vetores antes e depois
Guardam o “estado” da pasta antes e depois da verificação.

b) Lê o estado inicial
listar(antes, &nAntes);

c) Entra em um loop infinito
A cada 5 segundos:
	1.	Lê novamente a pasta → depois
	2.	Compara as duas listas procurando:
	•	Arquivos novos
	•	Arquivos modificados
	•	Arquivos removidos
	3.	Registra cada mudança com logar()
	4.	Atualiza o vetor “antes” para a próxima iteração


