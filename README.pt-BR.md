# Análise Estatística de Eficiência em Operações Logísticas com NumPy

[English](README.md) | [Português](README.pt-BR.md)

## Visão Geral

Este projeto apresenta uma análise estatística de operações logísticas simuladas utilizando Python e NumPy.

O objetivo é explorar como características operacionais, como distância percorrida, tempo de entrega, número de paradas e custo da rota, se relacionam e como a análise estatística pode apoiar a identificação de rotas de alto custo e operações mais eficientes.

A base de dados é totalmente sintética e foi criada especificamente para fins de estudo, experimentação e portfólio.

---

## Contexto de Negócio

Uma empresa de logística realiza um volume significativo de entregas e coleta informações operacionais sobre suas rotas, como distância percorrida, tempo de entrega, quantidade de paradas e custo total da operação.

Embora esses dados possam apoiar decisões operacionais, indicadores agregados nem sempre fornecem visibilidade suficiente sobre as características que diferenciam rotas de alto custo de operações mais eficientes.

Este projeto utiliza análise estatística para explorar essas relações e identificar padrões que possam apoiar o planejamento das rotas e o controle de custos.

---

## Perguntas de Negócio

A análise foi desenvolvida para responder a quatro perguntas principais:

1. Qual é o perfil operacional médio das rotas simuladas em termos de distância, tempo de entrega, número de paradas e custo?
2. Quais características diferenciam as rotas de alto custo da operação geral?
3. Existem rotas que percorrem distâncias acima da média e, ainda assim, apresentam custos abaixo da média?
4. Quais relações estatísticas existem entre distância percorrida, tempo de entrega, número de paradas e custo da rota?

---

## Dataset

A base contém **5.000 rotas logísticas simuladas**.

Cada rota possui quatro variáveis analíticas principais:

| Variável | Descrição |
|---|---|
| `distance_km` | Distância percorrida pela rota em quilômetros |
| `delivery_time` | Tempo total da entrega em minutos |
| `num_of_stops` | Quantidade de paradas realizadas durante a rota |
| `route_cost` | Custo operacional total simulado da rota |

Variáveis adicionais, como velocidade média, atraso operacional, custo por quilômetro e custo por parada, foram utilizadas somente durante o processo de simulação.

Foi utilizada uma semente fixa do NumPy (`100`) para garantir a reprodutibilidade dos resultados.

---

## Lógica da Simulação

As características das rotas foram geradas utilizando NumPy.

As distâncias foram simuladas aleatoriamente entre **10 e 300 km**.

A velocidade média das rotas variou entre **35 e 90 km/h**, enquanto os atrasos operacionais aleatórios ficaram entre **10 e 90 minutos**.

O número de paradas foi gerado independentemente entre **1 e 15 paradas por rota**.

O custo total foi calculado a partir da combinação de:

- distância percorrida;
- custo variável por quilômetro;
- número de paradas;
- custo variável por parada.

A proposta não foi impor previamente uma distribuição estatística ao custo final, mas permitir que a distribuição surgisse a partir das regras operacionais simuladas.

---

## Análise Estatística Descritiva

A operação simulada apresentou o seguinte perfil:

| Métrica | Resultado |
|---|---:|
| Distância Média | 155,44 km |
| Tempo Médio de Entrega | 210,17 min |
| Número Médio de Paradas | 7,99 |
| Custo Médio da Rota | R$ 744,46 |
| Mediana do Custo | R$ 718,32 |
| Desvio Padrão do Custo | R$ 355,52 |
| Menor Custo | R$ 58,19 |
| Maior Custo | R$ 1.787,44 |

Uma rota média percorre aproximadamente **155 km**, demanda cerca de **210 minutos**, ou 3h30, e realiza aproximadamente **8 paradas**.

O custo médio de **R$ 744,46** ficou ligeiramente acima da mediana de **R$ 718,32**, indicando uma leve assimetria à direita na distribuição dos custos.

O desvio padrão de **R$ 355,52** demonstra uma variação considerável entre os custos das diferentes rotas simuladas.

---

## Distribuição dos Custos das Rotas

![Distribuição dos Custos das Rotas](images/route_cost_distribution.png)

O histograma mostra uma maior concentração de rotas nas faixas intermediárias de custo, enquanto uma quantidade menor de operações mais caras prolonga a distribuição para valores superiores.

O intervalo de um desvio padrão em torno da média ficou aproximadamente em:

- **-1 DP:** R$ 388,94
- **Média:** R$ 744,46
- **+1 DP:** R$ 1.099,97

A média superior à mediana reforça a existência de uma leve cauda à direita.

A distribuição não apresenta um formato perfeitamente normal, o que é coerente com a construção do projeto: os custos não foram sorteados diretamente de uma distribuição normal, mas resultaram da combinação de diferentes variáveis operacionais.

---

## Rotas de Alto Custo

As rotas de alto custo foram definidas pelo seguinte critério estatístico:

```text
Custo da Rota > Custo Médio + 1 Desvio Padrão
```

O limite obtido foi de aproximadamente **R$ 1.099,97**.

Foram identificadas **880 rotas**, equivalentes a **17,6% da base**.

| Métrica | Operação Geral | Alto Custo | Diferença |
|---|---:|---:|---:|
| Distância Média | 155,44 km | 258,47 km | +66,3% |
| Tempo Médio de Entrega | 210,17 min | 318,33 min | +51,5% |
| Número Médio de Paradas | 7,99 | 9,48 | +18,6% |
| Custo Médio | R$ 744,46 | R$ 1.297,21 | +74,3% |

As rotas de alto custo apresentam principalmente distâncias significativamente maiores.

A distância média desse grupo é aproximadamente **103 km superior** à média geral, enquanto o tempo de entrega também aumenta de forma relevante.

O número médio de paradas cresce em menor proporção que a distância, sugerindo que a distância é uma característica mais marcante para diferenciar esse segmento na simulação.

---

## Rotas Operacionalmente Eficientes

Foram consideradas operacionalmente eficientes as rotas que atendem simultaneamente aos seguintes critérios:

```text
Distância > Distância Média
E
Custo da Rota < Custo Médio
```

Foram identificadas **338 rotas**, correspondentes a **6,76% da base**.

| Métrica | Operação Geral | Rotas Eficientes | Diferença |
|---|---:|---:|---:|
| Distância Média | 155,44 km | 185,75 km | +19,5% |
| Tempo Médio de Entrega | 210,17 min | 247,16 min | +17,6% |
| Número Médio de Paradas | 7,99 | 4,96 | -37,9% |
| Custo Médio | R$ 744,46 | R$ 646,59 | -13,1% |

Essas rotas percorrem distâncias aproximadamente **19,5% maiores que a média**, enquanto mantêm custos aproximadamente **13,1% menores**.

Uma das principais diferenças está no número de paradas: as rotas eficientes apresentam aproximadamente **38% menos paradas** que a média geral.

Esse resultado não demonstra que um número menor de paradas cause necessariamente custos menores, mas evidencia um perfil operacional diferente que poderia ser investigado em uma operação real.

---

## Análise de Correlação

![Matriz de Correlação](images/correlation_matrix.png)

A matriz apresentou as seguintes relações:

| Variáveis | Correlação |
|---|---:|
| Distância × Custo da Rota | **0,89** |
| Distância × Tempo de Entrega | **0,84** |
| Tempo de Entrega × Custo da Rota | **0,75** |
| Número de Paradas × Custo da Rota | **0,24** |
| Número de Paradas × Distância | **-0,01** |
| Número de Paradas × Tempo de Entrega | **-0,01** |

### Análise

A relação mais forte aparece entre **distância e custo da rota**, com coeficiente de correlação de **0,89**.

Isso representa uma associação linear positiva forte: na base simulada, rotas mais longas tendem a apresentar custos mais elevados.

A distância também possui relação forte com o tempo de entrega (`0,84`), resultado coerente com a forma como o tempo foi construído durante a simulação.

Tempo de entrega e custo apresentam correlação de `0,75`, indicando outra associação positiva forte.

Em contraste, o número de paradas possui apenas uma relação **fraca com o custo (`0,24`)** e praticamente nenhuma associação linear com distância ou tempo de entrega.

Como os dados são sintéticos, esses coeficientes refletem parcialmente as próprias regras da simulação e não devem ser tratados como evidência de causalidade.

---

## Distância vs Custo da Rota

![Distância vs Custo da Rota](images/distance_vs_route_cost.png)

### Análise

O gráfico de dispersão reforça visualmente a relação positiva identificada na matriz de correlação.

À medida que a distância aumenta, o custo das rotas também tende a crescer.

Entretanto, rotas com distâncias semelhantes podem apresentar custos bastante diferentes.

Essa dispersão ocorre porque o custo por quilômetro e o custo por parada variam entre as operações simuladas.

A variabilidade também aumenta nas maiores distâncias, produzindo uma faixa mais ampla de custos possíveis.

Portanto, a distância apresenta forte associação com o custo, mas não explica isoladamente toda a sua variação.

---

## Número de Paradas vs Custo da Rota

![Número de Paradas vs Custo da Rota](images/number_of_stops_vs_route_cost.png)

### Análise

A relação entre número de paradas e custo é significativamente mais fraca.

Para praticamente todas as quantidades de paradas existem rotas distribuídas por uma ampla faixa de custos.

Esse comportamento visual é coerente com o coeficiente de correlação de apenas **0,24**.

Embora o número de paradas participe do cálculo do custo, a distância e os custos relacionados aos quilômetros percorridos possuem influência significativamente maior na variação total observada.

---

## Percentis do Custo das Rotas

A distribuição apresentou os seguintes percentis:

| Percentil | Custo da Rota |
|---|---:|
| P25 | R$ 455,87 |
| P50 | R$ 718,32 |
| P75 | R$ 999,10 |
| P90 | R$ 1.239,25 |
| P95 | R$ 1.368,95 |

O limite utilizado para classificar as rotas de alto custo, **R$ 1.099,97**, ficou entre os percentis 75 e 90.

Como **17,6% das rotas ficaram acima desse limite**, o valor corresponde aproximadamente ao **percentil 82,4** da operação simulada.

Assim, o segmento de alto custo representa aproximadamente as **18% rotas mais caras da base**, sem a necessidade de definir arbitrariamente um valor monetário fixo.

---

## Principais Resultados

A análise apresentou cinco resultados principais:

- **A distância é a variável com maior associação ao custo da rota**, com correlação de `0,89`.
- As rotas de alto custo percorrem aproximadamente **66% mais distância** que a média geral.
- As rotas de alto custo representam **17,6%** da operação simulada.
- As rotas operacionalmente eficientes percorrem distâncias acima da média mantendo custos aproximadamente **13% inferiores**.
- O número de paradas apresenta associação linear significativamente menor com o custo total quando comparado à distância.

O projeto demonstra como estatística descritiva, segmentação, percentis, correlação e visualização podem transformar uma base logística relativamente simples em informações úteis para análise operacional.

---

## Implicações para o Negócio

Em uma operação logística real, análises desse tipo poderiam apoiar investigações relacionadas a:

- planejamento de rotas;
- monitoramento de custos;
- identificação de operações fora do padrão;
- comparação da eficiência entre rotas;
- investigação de direcionadores de custo;
- definição de benchmarks operacionais.

O objetivo deste projeto não é otimizar rotas nem prever custos futuros.

A proposta é construir uma base analítica que futuramente poderia ser expandida com técnicas de previsão, otimização, detecção de anomalias ou Machine Learning.

---

## Tecnologias

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## Estrutura do Projeto

```text
logistics_operations_statistical_analysis/
│
├── data/
│   └── README.md
│
├── images/
│   ├── route_cost_distribution.png
│   ├── correlation_matrix.png
│   ├── distance_vs_route_cost.png
│   └── number_of_stops_vs_route_cost.png
│
├── notebooks/
│   └── logistics_operations_analysis.ipynb
│
├── README.md
├── README.pt-BR.md
├── requirements.txt
└── .gitignore
```

---

## Executando o Projeto

Clone o repositório:

```bash
git clone <repository-url>
```

Crie o ambiente virtual:

```bash
python -m venv .venv
```

Ative o ambiente e instale as dependências:

```bash
python -m pip install -r requirements.txt
```

Abra:

```text
notebooks/logistics_operations_analysis.ipynb
```

e execute as células sequencialmente.

---

## Aviso

Todos os dados, regras operacionais, custos, limites e cenários utilizados neste projeto são fictícios.

O projeto foi desenvolvido exclusivamente para fins educacionais, experimentação e portfólio e não representa a operação de uma empresa real de logística.