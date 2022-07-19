# Gerenciador de Memória - SIN351
- **Aluno**: Rodolfo Brizzi Junior
- **Matrícula:** 6025
- **Link do repositório no GitHub:** https://github.com/rodbrizzi/simulador-memoria-virtual-351
## Objetivos

 - Introduzir os conceitos de Gerenciamento de Memória;
 - Familiarizar o estudante com as técnicas de Gerenciamento de Memória e Subistituição de Páginas dos Sistemas Operacionais Modernos;
 - Aprimorar as capacidades de programação em Linguagem C.

## Descrição:
Projeto proposto pelo professor Rodrigo Moreira, desenvolvido para a disciplina de Sistemas Operacionais - SIN351 da Universidade Federal de Viçosa - Campus Rio Paranaíba.
O professor disponibilizou um código "esqueleto" de um programa implementado em linguagem C, que possui a implementação básica do gerenciamento de memória.
A tarefa foi implementar os seguintes algoritmos de substituição de páginas:
- FIFO;
- FIFO + Bit R (Segunda Chance);
- NRU;
- Aging (Envelhecimento);

Após a implementação, foi realizada a comparação do desempenho de todos os algoritmos listados acima com o algoritmo de substituição de páginas Random (Aleatório), previamente disponibilizado pelo professor.

## Funcionamento
 - **FIFO:**
	- Mantém uma lista encadeada que contém todas as páginas
		-  página mais antiga fica no início da fila;
		-  página que chegou por último fica no fim da fila.
	- Quando ocorre page fault:
		- página no início da fila é removida;
		- nova página é adicionada no final da fila.
	-	 Desvantagem:
			- não leva em consideração se a página a ser removida é utilizada ou não com frequência.
	
 - **FIFO + Bit R (Segunda Chance):**
	- Modificação do FIFO
	-   Escolhe uma página para ser removida utilizando o FIFO
	-  Antes de remover a página, verifica o bit de referência:
	    -   Se for 0 a página é removida.
	    -   Se for 1, da uma segunda chance a página, e define o bit de referência como 0.
	- Vantagem: 
		- Melhor que o FIFO, pois leva em consideração se a página foi utilizada anteriormente.
	- Desvantagem:
		- Se todas as páginas forem referenciadas, o algoritmo degenera-se para FIFO.
		
 - **NRU**:
	- Cada página tem os bits R (referenciada) e M (modificada)
		- Os bits são colocados em 1 quando a página é referenciada e modificada
	- As páginas são classificadas, pelo sistema operacional em 4 classes:
		- Classe 0: não referenciada, não modificada;
		- Classe 1: não referenciada, modificada;
		- Classe 2: referenciada, não modificada;
		- Classe 3: referenciada, modificada;
	- NRU remove a página da classe mais baixa primeiro.

 - **Aging (Envelhecimento):**
	- Cada página possui um contador para controlar a frequência que a página é acessada
	- Contadores são sempre deslocados um bit para direita antes de serem somados com o bit R
	- Bit R é adicionado ao bit mais à esquerda do contador, ao invés de ser somado ao mais à direita
	- Quando ocorre falta de página:
		- SO escolhe a página com menor contador.
## Execução
Para executar o algoritmo é necessário utilizar os seguintes comandos: 

     gcc -Wall main.c -o main
     ./main "escolha" 10 < anomaly.dat
**OBS**: Substituir a escolha pelo algoritmo escolhido:

 - fifo
 - second-chance
 - nru
 - aging
 


