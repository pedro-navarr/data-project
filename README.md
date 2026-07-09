# ✈️ Análise Resiliente de Ocorrências Aeronáuticas no Databricks

Este projeto apresenta uma solução completa de dados (End-to-End) para a ingestão, tratamento, modelagem e visualização dos dados públicos e incidentes aeronáuticos e informaçoes de aeronaves da aviação civil brasileira, disponibilizados pelo gov.

A ideia deste projeto foi aplicar os conceitos de **Lakehouse** e **Arquitetura Medallion**, saindo do dado bruto até a construção de um dashboard interativo focado em inteligência de segurança operacional.

---

## 🏗️ Arquitetura do Projeto e Tecnologias

A pipeline foi desenvolvida integralmente dentro do ecossistema **Databricks**, utilizando **Spark SQL** e **Python/PySpark** para o processamento distribuído. O ciclo de vida dos dados seguiu a divisão em três camadas:

1. **Bronze (Ingestão):** Carga dos dados brutos e simulação das tabelas iniciais contendo o histórico de ocorrências, fator e dados das aeronaves (`aeronave`, 'fator e `ocorrencia`).
2. **Silver (Transformação & Qualidade):** Fase crítica de limpeza de dados. Foi realizada a padronização de strings, tratamento de valores nulos, conversão de tipos temporais e aplicação de regras rigorosas para remoção de resíduos e registros inválidos (como dados classificados como "NÃO INFORMADO").
3. **Gold (Regras de Negócio):** Modelagem de tabelas analíticas otimizadas para responder a perguntas estratégicas específicas, agregando dados por perfis de risco de modelos, sazonalidade temporal, localização geográfica e confiabilidade de componentes (motores).

---

## 📉 Visualização e Insights (Databricks SQL Dashboard)

Para fechar o ciclo do dado, foi construído um Dashboard SQL interativo composto por 5 visões estratégicas para tomada de decisão:

* **Distribuição Geográfica (Mapa de Coroplet):** Mapeamento do volume de ocorrências por estado brasileiro.
* **Ranking de Modelos Críticos:** Gráfico de barras horizontais detalhando quais modelos de aeronaves possuem maior volume de eventos e taxas de gravidade.
* **Sazonalidade Mensal:** Gráfico de linhas identificando picos históricos de ocorrências ao longo dos meses do ano.
* **Severidade das Ocorrências:** Gráfico de rosca (Donut Chart) avaliando a proporção de severidade do funil de segurança (Incidente vs. Incidente Grave vs. Acidente).
* **Tecnologia do Motor vs. Risco:** Gráfico de barras empilhadas (Stacked Bar Chart) cruzando os tipos de motorização com a gravidade dos eventos, provando visualmente a confiabilidade de tecnologias (como motores a jato vs. pistão).

---

## 🛠️ Lições Aprendidas e Desafios de Engenharia

* **Sintaxe e Debugging no Spark SQL:** Resolução de erros complexos de parser de execução (como tratamento do erro `[INVALID_EXTRACT_BASE_FIELD_TYPE]`, gerado por conflitos na extração de estruturas complexas).
* **Qualidade da Informação:** Tratamento de dados geográficos inconsistentes ou omissos para garantir a integridade visual e estatística do projeto.
* **Interatividade de Negócio:** Implementação de parâmetros globais no Dashboard (filtros por segmentos de mercado, como aviação agrícola ou instrução) para simular um ambiente real de operações e tomadores de decisão.

---

### 🚀 Como Visualizar
* Os notebooks com os códigos (Bronze, Silver e Gold) estão na logo acima.
