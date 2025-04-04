# Algoritmo Caminho Hamiltoniano
O algoritmo para encontrar um Caminho Hamiltoniano em um grafo pode ser implementado utilizando a técnica de backtracking, que explora todas as possibilidades de caminhos até encontrar uma solução válida. Um Caminho Hamiltoniano é aquele que visita cada vértice do grafo exatamente uma vez. Este método é aplicado tanto para grafos orientados quanto não orientados, desde que sejam representados como uma matriz de adjacência.

## Como funciona o algoritmo Caminho Hamiltoniano?
### Entrada do Usuário:
O programa solicita ao usuário que insira uma matriz de adjacência representando o grafo. A entrada deve ser fornecida no formato de uma lista de listas, onde cada elemento indica se há ou não uma conexão entre dois vértices. Por exemplo:

[[0, 1, 1, 0],
[1, 0, 1, 1],
[1, 1, 0, 1],
[0, 1, 1, 0]]
### Validação:
Se a entrada estiver malformada (não for uma matriz quadrada ou contiver valores inválidos), o programa exibe uma mensagem de erro e solicita que o usuário insira novamente a matriz.

## Execução do Algoritmo:
A função find_hamiltonian_path é chamada com a matriz de adjacência fornecida pelo usuário. O algoritmo tenta construir o caminho recursivamente, verificando se cada vértice pode ser adicionado ao caminho atual sem violar as condições de um Caminho Hamiltoniano. Se um caminho válido for encontrado, ele é exibido; caso contrário, o programa informa que não existe um Caminho Hamiltoniano no grafo.

## Ideia Principal
O código implementa o algoritmo de busca de Caminho Hamiltoniano utilizando backtracking. A ideia principal é explorar todos os possíveis caminhos no grafo, verificando se eles atendem às condições de um Caminho Hamiltoniano. O processo segue o princípio de tentar adicionar vértices ao caminho atual, retrocedendo quando uma escolha leva a um estado inválido.

Esse método é baseado na tentativa e erro, mas garante que todas as possibilidades sejam exploradas. Embora seja computacionalmente intensivo para grafos grandes, ele é eficiente para grafos menores e fornece uma solução exata.

## Lógica de Como foi Implementado
Linha 6-7: Caso base: verifica se todos os vértices foram visitados (o comprimento do caminho é igual ao número de vértices). Se verdadeiro, retorna o caminho.
Linha 10-15: Itera sobre todos os vértices do grafo e verifica se o vértice atual pode ser adicionado ao caminho usando a função is_valid.
Linha 16-18: Adiciona o vértice ao caminho e chama recursivamente a função para continuar construindo o caminho.
Linha 20-21: Se o caminho não for válido, remove o vértice do caminho (backtracking) e tenta outro vértice.
Linha 24: Retorna o resultado final (Caminho Hamiltoniano ou inexistência).

## Dependências
Nenhuma. O código utiliza apenas bibliotecas padrão do Python.

## Como Rodar o Projeto
### Passo 1: 
Execute o arquivo main.py em sua IDE ou terminal.

#### Passo 2: 
Insira a matriz de adjacência conforme solicitado pelo programa.

### Passo 3: 
Visualize o resultado (Caminho Hamiltoniano ou mensagem indicando que ele não existe).

## Versão do Python
Este projeto foi desenvolvido na versão 3.10.0 do Python.

## Análise da Complexidade Computacional
### Classes P, NP, NP-Completo e NP-Difícil:
O problema do Caminho Hamiltoniano pertence à classe NP-completo. Isso significa que, embora seja possível verificar rapidamente (em tempo polinomial) se uma solução dada é válida, encontrar essa solução exige explorar todas as combinações possíveis, o que torna o problema intratável para grafos grandes.

Essa classificação está diretamente relacionada ao Problema do Caixeiro Viajante (TSP), que também é NP-completo. No TSP, o objetivo é encontrar o menor ciclo que passa por todos os vértices, enquanto no Caminho Hamiltoniano, buscamos apenas um caminho que visite todos os vértices exatamente uma vez. Ambos exigem explorar todas as combinações possíveis de vértices, tornando-os computacionalmente difíceis.

### Análise da Complexidade Assintótica de Tempo:
A complexidade temporal do algoritmo é O(n!), onde (n) é o número de vértices no grafo. Isso ocorre porque o algoritmo precisa explorar todas as permutações possíveis dos vértices para verificar se algum deles forma um Caminho Hamiltoniano.

Essa complexidade foi determinada pela contagem de operações realizadas durante o processo de backtracking. Cada vértice gera (n-1) chamadas recursivas, e o processo continua até que todos os vértices sejam visitados. Como o número de permutações de (n) vértices é (n!), essa é a complexidade dominante.

### Aplicação do Teorema Mestre:
O Teorema Mestre não pode ser aplicado diretamente ao problema do Caminho Hamiltoniano, pois a recorrência associada ao algoritmo não segue o formato necessário para aplicação do teorema ((T(n) = aT(n/b) + f(n))). Em vez disso, o algoritmo realiza chamadas recursivas que dependem de permutações dos vértices, o que foge do escopo do Teorema Mestre.

Para aplicar o Teorema Mestre, seria necessário que o problema fosse dividido em subproblemas independentes com tamanho reduzido proporcionalmente ((n/b)), o que não acontece neste caso.

## Análise dos Casos de Complexidade:
### Pior Caso:
O pior caso ocorre quando o grafo não possui um Caminho Hamiltoniano. Nesse cenário, o algoritmo precisa explorar todas as combinações possíveis de vértices antes de concluir que nenhum caminho válido existe. A complexidade é (O(n!)).

### Caso Médio:
No caso médio, assumimos que o grafo tem características aleatórias. O desempenho ainda será dominado pela necessidade de explorar múltiplas combinações, mas o número de combinações pode ser menor dependendo da estrutura do grafo. A complexidade permanece próxima de (O(n!)).

### Melhor Caso:
O melhor caso ocorre quando o primeiro caminho testado já é um Caminho Hamiltoniano. Nesse caso, o algoritmo termina rapidamente, realizando apenas (O(n)) operações para validar o caminho.

## Impacto no Desempenho:
As diferenças entre os casos impactam diretamente o tempo de execução do algoritmo. Para grafos pequenos ou bem estruturados, o algoritmo pode ser eficiente. No entanto, para grafos grandes ou densos, o tempo de execução cresce exponencialmente, tornando-o impraticável para uso em sistemas reais sem heurísticas ou otimizações adicionais.
