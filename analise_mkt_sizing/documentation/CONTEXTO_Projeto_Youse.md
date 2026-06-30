# Contexto Geral — Projeto Youse (Control Tower de Clientes)

> Documento de contexto para uso em agentes de IA executando tarefas variadas do projeto.
> Baseado na proposta final **aceita** pela Youse (A&M Performance, 30/abr/2026).
> Cliente: **Youse** (insurtech). Consultoria: **A&M Performance / Alvarez & Marsal** (time Digital & AI LATAM).

---

## 1. Resumo executivo (1 parágrafo)

A Youse construiu vantagem em experiência digital, mas a pressão competitiva exige trocar o motor de crescimento de **"volume-led"** (aquisição por volume) para **crescimento orientado por valor**. Os indicadores apontam **seleção adversa na entrada** (base grande de perfis menos desejáveis), gerando **CAC elevado, churn alto, custo de servir acima do benchmark e IC (Índice Combinado) ~103%**. A A&M vai redesenhar a estratégia de clientes como um **sistema operacional baseado em personas comportamentais**, onde cada decisão de aquisição, relacionamento, retenção e oferta é guiada por (i) valor futuro (LTV), (ii) risco (sinistro/atendimento), (iii) propensão (conversão/renovação) e (iv) canal preferencial. A execução é suportada por um **CRM operado por agentes de IA**, escalando com baixo headcount.

---

## 2. Problema e objetivos

### Dores atuais (hipóteses validadas no diagnóstico inicial)
- **Visão estratégica generalista** — baixo entendimento do comportamento do cliente, baixa previsibilidade estratégica.
- **Pouca eficiência na venda** — qualidade ruim dos clientes que entram na base.
- **Baixo retorno do CRM** — campanhas pouco efetivas.
- **Churn elevado** — carteira com retenção baixa e pouca assertividade.
- **Preço reativo e não preditivo** (OPCIONAL / fora do escopo) — precificação que só ajusta após ver resultados.

### Objetivos do projeto
1. Desenho da proposta de valor e estratégia de clientes **segmentada por persona** (valor econômico, risco, comportamento).
2. Apoio ao desenvolvimento de um **CRM agêntico** (jornadas, campanhas, next-best-action por persona).
3. **Governança orientada a impacto** — métricas, baseline, experimentação A/B, acompanhamento de resultados no P&L.
4. (Fora do escopo) Operacionalização em **subscrição e pricing** — modelos preditivos, risco dinâmico, decisões por valor.

---

## 3. Conceito central: Persona como unidade operacional

Cada modelo deixa de ser "um modelo para todos" e passa a ser **"um modelo por comportamento"**. As personas são **data-driven** (criadas via ML/IA sobre dados exaustivos do cliente), não demográficas amplas.

### Dimensões de cada persona
- **Valor:** LTV esperado, margem esperada.
- **Risco e custo de servir:** propensão a sinistro, frequência de contato, mapeamento do custo de servir por recorte.
- **Propensão:** conversão, renovação, cross-sell, churn.
- **Canal e momento de vida:** preferência de canal, gatilhos comportamentais, jornada do cliente.

### Implicação prática (o que a persona direciona)
Intensidade de abordagem · oferta adequada · canal prioritário · nível de incentivo · política de risco/preço · modelo de atendimento.

### Fontes de dados para construção das personas
Histórico de apólices (produtos, renovações, upgrades, cross-sell); histórico de sinistros (frequência, severidade, causas); dados demográficos; interações online; bureaux de crédito; geoposicionamento.

**Atributos críticos modelados:** renda, tipos/regiões de gastos, usos e volume de crédito, tempo entre compras (P/M/G), tempo entre cliques, "bom pagador?", regiões de convívio (geo-risco), probabilidade de compra, risco de carrinho abandonado, rebotes, etc.

**ID único do cliente:** hoje a chave usada é o **e-mail**; o projeto cria um ID único deduplicado e higienizado.

---

## 4. Catálogo de Produtos de Dados (o "produto" entregue)

Organizado em 3 etapas. **Risk & Pricing está fora do escopo** da Fase I.

### Etapa 1 — Fundamentos Analíticos
| Produto | Quem usa | Valor |
|---|---|---|
| Visão 360 | Analistas de dados, BI | Visão unificada do cliente; base para análises |
| Pirâmide Clientes | Gestores de risco, produto | Visões multidimensionais (risco, sinistro, produto) |
| Análise Base e Mkt Sizing | Marketing, produto | Caracterização em tempo real da base |
| Análise Estocástica | Atuários, risco | Previsão de comportamento futuro |
| Clustering, Personas | Marketing, CRM | Grupos comportamentais; transições entre perfis |
| Ranking | Estratégia, produto, marketing | Segmentação por valor e comportamento |

### Etapa 2 — Estado-da-Arte e Orquestração
| Produto | Quem usa | Valor |
|---|---|---|
| LTV & CAC | Financeiro, marketing | Comparação valor vs. custo por cliente; ranqueamento de rentabilidade |
| Life Cycle | CRM, marketing | Next Best Action/Offer por fase do ciclo |
| BP CRM e Agentes CRM | Vendas, atendimento | Operacionalização de NBA/NBO; abordagem personalizada |

### Etapa 3 — Risk & Pricing (FORA DO ESCOPO)
| Produto | Quem usa | Valor |
|---|---|---|
| Risco Probabilístico | Subscrição, pricing | Risco em tempo real por cliente |
| Preço Dinâmico | Pricing, subscrição | Preço personalizado por CPF/persona |

### A tríade de quantificação (Orquestração e governança)
- **CAC preditivo por persona** — custo total de trazer aquele perfil até a apólice ativa (canal, touchpoints, conversão histórica).
- **LTV por persona** — contribuição líquida esperada ao P&L ao longo do ciclo de vida (não é o prêmio pago). Com IC ~103%, muitos clientes têm **LTV negativo** — o modelo torna isso visível **antes da entrada**.
- **Ranking de Clientes** — score de retorno esperado por real investido; dinâmico, muda conforme a carteira evolui.

### Life Cycle
Combina Pirâmide (onde a base está) + Personas (quem são/como se comportam) + CAC/LTV (custo e valor). Projeta a carteira em 3/6/12 meses, calcula valor econômico esperado por perfil, e entrega visão prospectiva + critério de entrada por valor (não volume) + alavancas prescritivas de retenção ancoradas no P&L.

---

## 5. CRM Agêntico (arquitetura)

**Blueprint de CRM (o quê):** Calendário de Ações · NBO/NBA por persona · Testes A/B.

**Comitê Agêntico de CRM (como)** — pipeline de agentes com human-in-the-loop:
`Dados e Objetivos → Agente Segmentação → Agente Estratégia → Agente Criativo → Agente Orquestrador → Agente Governança → Agente Experimentação → Execução Campanha → Mensuração Resultados`

Objetivo: operação coesa, assistida por humanos no loop, evolutiva.

---

## 6. Metodologia de implantação

### Fases de maturação de cada produto de dados
**MVP → PILOTO → PRODUÇÃO**
- **MVP (Necessidade):** processo mapeável? dados suficientes? modelos viáveis? arquitetura existe? ganhos potenciais? factível?
- **PILOTO (Cuidado):** o que melhorar, em que ordem, em quanto tempo, com quais modelos, usados por quem, com que retorno?
- **PRODUÇÃO (Consequência):** uso perene, resultados mensurados, ganhos quantificados, modelos atualizados, processo sustentável.

### Construção de um produto de dados (esteira técnica)
Deep Dive no Processo → Estruturação dos Dados + Diagrama de Tempos e Movimentos → Criação do modelo de dados → Modelos Candidatos ⇄ Otimização Paramétrica ⇄ Treinamento em Dados Históricos → Best Performer → Teste em Novos Dados (MVP) → Uso Assistido (PILOTO) → Tombamento em Produção.

### Uso assistido vs. produção
- **Uso assistido:** esteira **paralela**; produto em teste A/B + teste de estresse; monitorado pelos times **A&M + Youse**. Avalia 3 perguntas: (1) comporta-se com novos dados como no treino? (2) lida com casos novos? (3) é consistente sob uso severo?
- **Produção:** esteira **de negócios**; operada de forma **plenamente autônoma pela Youse**, capacitada para melhorias/manutenções.

### Pipeline técnico (Visão 360)
Fontes de dados → Camada de Integração (ID único deduplicado/higienizado, acesso, regras de transformação, carga) → Visão 360 (perfil, relacionamento, contratos, sinistros) → Motores de decisão e consumo (modelos, agentes, dashboards).
- **Desenho:** A&M define produto, arquitetura analítica, lógica de negócio/KPIs, especificação técnica; Youse apoia e valida.
- **Construção:** A&M constrói tabelas/modelos, treina, versiona e valida; Youse apoia, valida, produtiza e executa em produção.

---

## 7. Estrutura de frentes e cronograma

### Frentes de trabalho
| Frente | Conteúdo | Fase |
|---|---|---|
| **A** | Visão 360, Pirâmide Clientes | I |
| **B** | Análise Base Cli., Análise Estocástica, Clustering | I |
| **C** | Personas, Ranking Clientes | I |
| **D** | CAC, LTV, Life Cycle | I |
| **E** | BP CRM, Agentes, Operação Paralela | I |
| **F** | Risco Probabilístico, Sensibilidade de preço, Preço Dinâmico | II (OPCIONAL, fora do escopo) |

### Linha do tempo
- **Fase I (escopo da proposta):** Frentes A–E.
  - Duração de referência no cronograma de alto nível: **6 meses** (Fundamentos Analíticos ~6m + Estado-da-Arte/Orquestração ~3m, com sobreposição).
  - **Tempo estimado contratado: 6 meses.**
  - Detalhamento funcional: ID universal/Visão 360/Pirâmide V1 (~1 mês) → Análise Base/Estocástica/Mkt Sizing/Clustering/Pirâmide V2 (~2 meses) → Personas/Ranking (~1 mês) → Life Cycle/CAC/LTV (~1 mês) → BP CRM/Agentes (~2 meses).
  - Frentes A,B,C em sprints (16 sprints ilustrativos); Frentes D,E em 8 sprints.
- **Fase II (fora do escopo):** Frente F, **3 meses**, em paralelo à Frente E. 12 sprints ilustrativos.

> ⚠️ Atenção a uma inconsistência interna da proposta: o cronograma de alto nível soma 6+3 meses, mas o "tempo estimado" comercial da Fase I é declarado como **6 meses**. Confirmar a baseline real de prazo antes de usar em planejamento.

---

## 8. Papéis e equipe

Três times sempre sincronizados: **Técnico** (constrói), **Negócio** (define valor esperado), **Sponsors** (executivos, garantem andamento e adoção). Cada time deve ter talentos de **A&M e Youse**.

**Composição por frente (Fase I):**
- 1 Diretor: PMO & QA (A&M) — em todas as frentes.
- DS (Data Scientist): 2 em A/B/C/E (Modelagem, Visão Sis., Otimização; Modelagem Agêntica na E), 1 na D — A&M.
- SR DE (Senior Data Engineer): ETL, Pipelines e Produtização — 2 por frente, majoritariamente **Youse** (na Frente A são A&M; participação Youse é necessária para extração/validação/produtização dos dados).
- 1 Consultor de Negócios (Reg. Neg.) — A&M (ausente na Frente D).

**Requisitos funcionais (recorrentes):** disponibilidade do time Youse; pleno acesso a dados íntegros da Youse; viabilidade positiva dos dados avaliada pela A&M; compatibilidade de arquitetura; deploy de modelos/produtos pelo time Youse. Para Fase II: permissão para esteira de agentes em nuvem; **Salesforce implantado** com pipeline de ingestão de CRM, camada analítica e APIs/MCPs para operação agêntica.

---

## 9. Proposta comercial (Fase I)

- **Escopo:** Frentes A, B, C (Produtos de Dados Client Centric) + D (CAC, LTV, Ciclo de Vida) + E (CRM Agêntico).
- **Tempo estimado:** 6 meses.
- **Honorários (Valor Fixo):**
  - **R$ 3.033.053,35** — valor líquido de impostos, sem despesas.
  - **R$ 3.320.255,45** — valor bruto (alíquota 8,65%), sem despesas.
- **Forma de pagamento:** 30% na assinatura · 30% na semana 10 · 30% na semana 18 · 10% no término (antes do suporte estendido).
- **Condições especiais (mutuamente excludentes):**
  - **A — Suporte estendido:** 1 consultor part-time (40h/mês) por 9 meses para validação de hipóteses, mensuração de resultados e exploração de erros/anomalias + liderança técnica ad-hoc.
  - **B — Pagamento dividido entre budgets 2026 e 2027:** o que exceder BRL 2.250.000 vai para o ano seguinte (ex. jul/2027).
- **Assinatura:** Rodrigo Carniato, Managing Director.

---

## 10. Resultados de negócio esperados (KPIs por frente)

- **Frente A/B (caracterização):** aumento de prêmio por cluster ↑; queda na sinistralidade por comportamento ↓; precisão de projeção de churn ↑; cross-sell mapeados ↑.
- **Frente C (personas/ranking):** LTV médio por persona ↑; CAC por persona ↓; LTV/CAC por persona ↑; ROAS de campanhas por persona ↑; IC por persona conhecido.
- **Frente D (orquestração):** renovação x persona ↑; churn x persona ↓; conversão NBO/NBA ↑; custo de servir x persona ↓; throughput de campanhas ↑; TTM de campanhas ↓.
- **Frente F (opcional):** sinistralidade ↓; aceitação de proposta ↑; margem x persona ↑; elasticidade x persona ↑; **IC ↓**.

### Impacto comparado por área (ilustrativo, modelos COM vs. SEM personas)
Marketing (adesão por produto ↑) · Vendas (corretores medianos → top performers) · Cross/Up-sell (+20% conversão incremental) · Subscrição (2–5 p.p. de melhora no Loss Ratio) · Pricing (+10–20% margem incremental) · Renovação (+8–12 p.p.) · Churn (−14% churn crítico) · Sinistros (−5–12% custo por sinistro) · Fraude (>15% de perdas evitáveis contidas).

---

## 11. Evolução das estratégias de precificação (referência conceitual)

Sequência de maturidade (1→6): Preços Uniformes → Preços por Segmentos de Risco → **Safra da Carteira de Segurados** (onde a Youse está hoje — preços futuros definidos pelo comportamento de safras passadas) → Carteira Fechada de Segurados → LTV em carteiras multiprodutos → **Carteira Preditiva e Preço Dinâmico (prescritivo)**. Os estágios 3–6 (Risk & Pricing) estão **fora do escopo** atual.

---

## 12. Glossário / vocabulário do projeto

- **IC (Índice Combinado):** sinistros + despesas sobre prêmios; ~103% = carteira operando no prejuízo técnico.
- **LTV / CAC:** valor do tempo de vida do cliente / custo de aquisição.
- **NBA / NBO:** Next Best Action / Next Best Offer.
- **Loss Ratio / Sinistralidade:** sinistros sobre prêmios.
- **Persona:** agrupamento comportamental data-driven (não demográfico) que funciona como unidade operacional de decisão.
- **Visão 360:** camada de dados unificada por cliente (ID único).
- **Pirâmide de Clientes:** visão multidimensional (risco, sinistro, produto).
- **Uso Assistido (PILOTO):** esteira paralela, A&M + Youse, com A/B e teste de estresse.
- **Produção:** esteira de negócios, operada autonomamente pela Youse.
- **Squad Técnico A&M:** time que constrói os produtos de dados.
- **MCP / APIs:** interfaces para a operação agêntica do CRM (Salesforce na Fase II).

---

## 13. Notas para uso por agentes

- **Idioma:** Português (Brasil), registro executivo.
- **Setor:** seguros / insurtech (auto é produto âncora; há "Reside" e cross-sell multiproduto).
- **Stakeholder A&M assinante:** Rodrigo Carniato (MD). Time A&M LATAM Digital & AI.
- **Fronteira de escopo:** Risk & Pricing / Preço Dinâmico (Frente F) é **opcional e fora do escopo contratado** — não assumir como entregue salvo confirmação.
- **Ponto aberto:** divergência de prazo Fase I (6m comercial vs. 6+3m no alto nível) — checar antes de planejar.
- **Pré-requisitos críticos de dados:** acesso íntegro aos dados Youse, ID único, viabilidade avaliada pela A&M, deploy pelo time Youse.
