# Otimização de Rotas de Entrega de Garrafões de Água com Algoritmos Genéticos (VRP-CC)

1. Visão Geral do Projeto

Este projeto acadêmico implementa um sistema de otimização de rotas de entrega para uma distribuidora de garrafões de água, utilizando Algoritmos Genéticos (AGs).
O desafio abordado é o **Problema de Roteamento de Veículos com Restrição de Capacidade Homogênea (HVRP-CC)**.
O objetivo principal é minimizar a distância total percorrida pela frota de veículos, garantindo que a capacidade de cada veículo seja respeitada.

2. O Problema (VRP-CC)

O problema consiste em determinar as rotas mais eficientes para múltiplos veículos que partem de uma distribuidora, visitam um conjunto de clientes para entregar garrafões de água e retornam à distribuidora.
A restrição fundamental é que cada veículo tem uma capacidade máxima de 6 garrafões (ou 6 paradas, assumindo 1 garrafão por parada).
A otimização busca reduzir custos operacionais, tempo de entrega e impacto ambiental.

2.1. Estrutura do Algoritmo Genético

O Algoritmo Genético é configurado com os seguintes componentes:

* **Otimização:** Minimizar a distância total percorrida pela frota de veículos.
* **Variável de Otimização:** A sequência de visitas dos clientes e a alocação de clientes para cada veículo.
* **Representação da Solução (Genoma/Cromossomo):** Uma permutação dos IDs dos clientes, com o ID `0` (zero) atuando como um separador para indicar o retorno do veículo ao depósito e o início de uma nova rota por outro veículo. Exemplo: `[Cliente1, Cliente2, Cliente3, 0, Cliente4, Cliente5]`.
* **Função de Aptidão (Fitness):** Calculada como o inverso do custo total. O custo total é a soma da distância total percorrida por todas as rotas válidas mais uma penalidade por qualquer violação da capacidade do veículo. Isso garante que soluções válidas e mais curtas tenham maior aptidão.
* **Método de Seleção:** **Seleção por Torneio (Tournament Selection)**. Indivíduos são selecionados aleatoriamente para um "torneio", e o indivíduo com a melhor aptidão vence e se torna um pai.
* **Método de Crossover (Cruzamento):** **Partially Mapped Crossover (PMX)**. Este operador é adaptado para problemas de permutação, garantindo que todos os clientes sejam visitados uma única vez. Ele recombina segmentos de rotas dos pais e reintroduz os separadores de depósito heuristicamente.
* **Método de Inicialização:** **Inicialização Aleatória Heurística**. A população inicial é gerada com permutações aleatórias de clientes e inserções heurísticas de separadores para formar rotas que tentam respeitar a capacidade desde o início, promovendo diversidade.
* **Critério de Parada:** **Número Máximo de Gerações**. O algoritmo executa por um número predefinido de gerações (padrão de 500 a 1000) e retorna a melhor solução encontrada até o final.

2.2. Gráficos de Convergência

Ao final da execução, o algoritmo irá exibir gráficos mostrando a melhor aptidão e a melhor distância encontrada por geração.

* **Melhor Aptidão por Geração:** Espera-se uma linha ascendente que se estabiliza, indicando que a qualidade da solução está melhorando.
* **Melhor Distância por Geração:** Espera-se uma linha descendente que se estabiliza, mostrando a redução da distância total das rotas.
