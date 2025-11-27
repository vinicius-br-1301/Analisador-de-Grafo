RELATÓRIO TÉCNICO: ANALISADOR DE PROPRIEDADES ESTRUTURAIS DE GRAFOS

1. DESCRIÇÃO GERAL

O software desenvolvido é uma ferramenta computacional com Interface Gráfica construída em Java. Seu objetivo é permitir a modelagem, visualização e análise de grafos não direcionados. O sistema classifica grafos com base em duas propriedades fundamentais: conectividade (número de componentes conexos) e ciclicidade (existência de ciclos).

2. REPRESENTAÇÃO INTERNA

Para maximizar a eficiência em grafos esparsos (onde o número de arestas é muito menor que o quadrado do número de vértices), optou-se pela utilização de uma Lista de Adjacência.
Estrutura de Dados: Map<Integer, List<Integer>> (HashMap).
Justificativa: O mapa permite o uso de vértices com rótulos inteiros não sequenciais (ex: vértice 1 conectado ao 100) sem o desperdício de memória que ocorreria em uma Matriz de Adjacência.
3. ESPECIFICAÇÃO DA ENTRADA E SAÍDA

3.1. Entrada (Input)

O programa aceita dados através de um componente de texto (JTextArea).
Formato: Lista de arestas, uma por linha.
Sintaxe: Origem-Destino (ou separados por espaço/vírgula).
Tipo de Dados: Inteiros (int).
Exemplo:
        1-2
        2-3
        3-1
        4-5
Interpretação: Um triângulo (ciclo) entre 1, 2 e 3, e uma aresta isolada entre 4 e 5.
3.2. Saída (Output)

O sistema fornece dois tipos de saída simultâneas:

A. Saída Analítica (Texto):
Contagem de Componentes Conexos: Um número inteiro representando grupos isolados de vértices.
Verificação de Ciclo: Um valor booleano (SIM/NÃO).
Classificação Final: Uma string combinando as propriedades (ex: "O grafo é Desconexo e Cíclico" ou "O grafo é Conexo e Acíclico (Árvore)").
B. Saída Visual (Gráfica):
Renderização do grafo em um painel JPanel customizado.
Layout: Circular (vértices distribuídos equidistantemente em um círculo).
Elementos: Vértices representados por círculos azuis numerados e arestas por linhas cinzas.
4. METODOLOGIA ALGORÍTMICA

Para a extração das propriedades, utilizou-se o algoritmo de Busca em Profundidade (DFS)
Conectividade: O algoritmo realiza iterações sobre a lista de vértices. Ao encontrar um vértice não visitado, incrementa o contador de componentes e executa uma DFS completa para marcar todos os vértices alcançáveis a partir dele.
Ciclicidade: Durante a execução da DFS, o algoritmo mantém o rastreamento do vértice "pai" (de onde veio a chamada recursiva). Se a busca encontrar um vértice vizinho que já foi visitado e que não é o pai imediato, confirma-se a existência de uma "aresta de retorno", caracterizando um ciclo.
5. ANÁLISE DE COMPLEXIDADE

Considerando V como o número de vértices e E como o número de arestas:

5.1. Complexidade de Tempo
Construção do Grafo: A inserção de cada aresta no HashMap e na ArrayList tem complexidade média constante O(1). Para E arestas, o tempo é O(E).
Análise (DFS): O algoritmo de Busca em Profundidade visita cada vértice e cada aresta, no máximo, duas vezes (uma por cada extremidade na lista de adjacência).
Pior Caso: O(V + E)
Esta complexidade é linear em relação ao tamanho do grafo, que é eficiente.
5.2. Complexidade de Espaço
Armazenamento (Lista de Adjacência): É necessário armazenar cada vértice e suas conexões. Em um grafo não direcionado, cada aresta aparece duas vezes (uma para a origem, outra para o destino).
Espaço: O(V + 2E) ≈ O(V + E)
Pilha de Recursão (DFS): No pior caso (um grafo que é uma linha longa), a pilha de recursão pode crescer até a profundidade V.
Espaço Auxiliar: O(V)
6. REQUISITOS DE SISTEMA E FERRAMENTAS
Linguagem: Java
Bibliotecas:
java.util.* (Coleções: List, Map, Set).
javax.swing.* (Interface Gráfica: JFrame, JPanel, JButton).
java.awt.* (Desenho e Layouts).
Paradigma: Orientação a Objetos.
7. CONCLUSÃO

O software funciona satisfatoriamente, implementando a estrutura de dados de grafos e algoritmos de percurso. A complexidade linear O(V + E) garante que a aplicação seja viável para grafos de tamanho moderado, enquanto a interface gráfica facilita a validação visual das estruturas de dados.
