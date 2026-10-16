## 1. Definição do Problema de Negócio
  [Português](README.pt-BR.md)  |  [English](README.md)

### 1.1. Contexto

Uma empresa de logística realiza diariamente um volume significativo de entregas e coleta diferentes informações operacionais sobre suas rotas, como distância percorrida, tempo de entrega, quantidade de paradas e custo final da operação.

Apesar da disponibilidade desses dados, parte das decisões relacionadas ao planejamento das rotas, controle de custos e eficiência operacional ainda é realizada com base em análises agregadas ou na experiência das equipes, sem uma compreensão estatística mais aprofundada sobre os fatores associados ao desempenho das operações.

---

### 1.2. Problema de Negócio

A empresa enfrenta o desafio de compreender quais características operacionais diferenciam as rotas de maior custo das rotas mais eficientes.

Essa falta de visibilidade pode resultar em:

- **Custos Operacionais Elevados:** Sem uma análise estruturada dos dados, torna-se mais difícil identificar quais características das rotas estão associadas ao aumento dos custos de transporte.

- **Baixa Eficiência Operacional:** Rotas com distâncias semelhantes podem apresentar tempos, número de paradas e custos significativamente diferentes, indicando possíveis oportunidades de otimização.

- **Dificuldade na Identificação de Padrões:** A ausência de uma análise quantitativa limita a capacidade de identificar grupos de rotas com características específicas, como operações de alto custo ou rotas com maior eficiência operacional.

- **Decisões Pouco Embasadas:** O planejamento logístico pode ser realizado sem uma visão clara sobre quais variáveis apresentam maior associação com o custo final das operações.

---

### 1.3. Objetivo Principal

Utilizar análise estatística dos dados operacionais para compreender o comportamento das rotas de entrega, identificar características associadas aos maiores custos e segmentar operações com diferentes níveis de eficiência.

A análise busca fornecer insights que possam apoiar decisões relacionadas ao planejamento de rotas, controle de custos e melhoria da eficiência operacional.

---

### 1.4. Perguntas-Chave a Serem Respondidas

A análise de dados deve responder às seguintes perguntas de negócio:

- **1 - Qual é o perfil médio das rotas em termos de distância percorrida, tempo de entrega, quantidade de paradas e custo operacional?**

- **2 - Quais são as principais características das rotas classificadas como de "Alto Custo"? Elas percorrem maiores distâncias, possuem mais paradas ou apresentam maior tempo de entrega?**

- **3 - Existem rotas com alta utilização operacional, como maiores distâncias ou maior número de paradas, mas que apresentam custos relativamente baixos? Quais características diferenciam essas operações?**

- **4 - Existe correlação estatisticamente relevante entre distância percorrida, tempo de entrega, quantidade de paradas e custo final da rota?**

---

### 1.5. Resultado Esperado e Impacto no Negócio

O resultado deste projeto será uma análise estatística das operações logísticas que permitirá:

- **Segmentação Operacional:** Identificar diferentes grupos de rotas, como "Rotas de Alto Custo" e "Rotas Operacionalmente Eficientes", permitindo análises mais direcionadas.

- **Identificação de Fatores Associados ao Custo:** Avaliar quais características operacionais apresentam maior relação com o custo final das rotas.

- **Otimização das Operações:** Identificar padrões que possam apoiar futuras iniciativas de melhoria no planejamento de rotas, distribuição de paradas e utilização dos recursos logísticos.

- **Suporte à Tomada de Decisão:** Fornecer uma base quantitativa para decisões relacionadas ao controle de custos e eficiência operacional, reduzindo a dependência exclusiva de análises agregadas ou percepção operacional.

- **Base para Análises Futuras:** Criar uma estrutura inicial que possa posteriormente ser expandida com técnicas de previsão, otimização ou Machine Learning.