# Documentação das Tabelas — Base de Dados SES/SUSEP

> A partir do mês de referência **abril/2013**, a base de dados do SES passou a ser disponibilizada no formato **Comma Separated Values (.csv)**, em conformidade com os padrões de interoperabilidade do Governo Eletrônico (e-Ping). Cada tabela corresponde a um arquivo com extensão `.csv`.

---

## Índice

| Arquivo | Descrição |
|---|---|
| [LimiteRetProxVig.csv](#limiteretproxvigcsv) | Seguradoras: Limite de Retenção |
| [Ses_campos.csv](#ses_camposcsv) | Tabela de campos (de/para para tabelas de valores) |
| [Ses_cessoes_recebidas.csv](#ses_cessoes_recebidascsv) | Resseguro: Movimentação por Cessionária |
| [Ses_cias.csv](#ses_ciascsv) | Cias do Mercado |
| [Ses_Contrib_Benef.csv](#ses_contrib_benefcsv) | Valores de Contribuições e Benefícios |
| [Ses_pl_margem.csv](#ses_pl_margemcsv) | Patrimônio Líquido e Margem de Solvência |
| [ses_prev_trad_resgates.csv](#ses_prev_trad_resgatescsv) | Previdência Tradicional — Resgates |
| [SES_prov_segprev.csv](#ses_prov_segprevcsv) | Seguradoras: Provisão das Operações de Previdência |
| [Ses_ramos.csv](#ses_ramoscsv) | Ramos de Seguros (tabela de referência) |
| [SES_Balanco.csv](#ses_balancocsv) | Valores de Balanço / Demonstração |
| [ses_cap_uf.csv](#ses_cap_ufcsv) | Capitalização — Dados por UF |
| [ses_contatos.csv](#ses_contatoscsv) | Contatos das Entidades |
| [ses_gruposramos.csv](#ses_gruposramoscsv) | Grupos de Ramos (tabela de referência) |
| [ses_pgbl_contrib.csv](#ses_pgbl_contribcsv) | PGBL — Contribuições |
| [ses_pgbl_fundos.csv](#ses_pgbl_fundoscsv) | PGBL — Fundos |
| [ses_pgbl_resgates.csv](#ses_pgbl_resgatescsv) | PGBL — Resgates |
| [ses_pgbl_uf.csv](#ses_pgbl_ufcsv) | PGBL — Dados por UF |
| [ses_prev_cap_uf.csv](#ses_prev_cap_ufcsv) | Previdência Capitalização — Dados por UF |
| [ses_prev_uf.csv](#ses_prev_ufcsv) | Previdência — Dados por UF |
| [ses_provramos.csv](#ses_provramoscsv) | Seguradoras: Provisão por Ramo |
| [ses_quantcap.csv](#ses_quantcapcsv) | Capitalização — Quantitativos |
| [ses_quantprev_benef.csv](#ses_quantprev_benefcsv) | Previdência — Quantitativo de Beneficiários |
| [ses_quantprev_part.csv](#ses_quantprev_partcsv) | Previdência — Quantitativo de Participantes |
| [ses_transferenciasexternas.csv](#ses_transferenciasexternascsv) | Transferências Externas |
| [SES_UF2.csv](#ses_uf2csv) | Seguros: Prêmios e Sinistros por UF |
| [SES_VALORESRESMOVGRUPOS.csv](#ses_valoresresmovgruposcsv) | Resseguros: Prêmios Ganhos e Sinistros Retidos |
| [Ses_vgbl_fundos.csv](#ses_vgbl_fundoscsv) | VGBL — Provisão Matemática de Benefícios a Conceder (Fundos) |
| [SES_ValoresMovRamos.csv](#ses_valoresmovramoscsv) | Mapas Demonstrativos de Prêmios, Sinistros e Custos de Aquisição |
| [Ses_RMovRam.csv](#ses_rmovramcsv) | ~~Tabela descontinuada~~ (desde 2014) |
| [Ses_seguros.csv](#ses_seguroscsv) | Seguros: Prêmios e Sinistros |

---

## LimiteRetProxVig.csv

**Descrição:** Seguradoras: Limite de Retenção

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `noenti` | Nome da Empresa |
| `coramo` | Código do Ramo no FIP |
| `valor` | Valor do limite de retenção |
| `damesano` | Ano e mês da informação |
| `pesrazaosocial` | Nome do administrador |
| `dircargo` | Cargo que ocupa |

---

## Ses_campos.csv

**Descrição:** Tabela com os campos para serem associados às tabelas de valores: `SES_ValoresMovRamos`, `SES_VALORESRESMOVGRUPOS` e `SES_BALANCO`.

> Utilizar fazendo join de `NUITEM` (Ses_campos) com `CMPID` das tabelas de valores.

| Campo | Descrição |
|---|---|
| `nuitem` | Número do Campo (chave de join com `CMPID`) |
| `noitem` | Nome do Campo |

---

## Ses_cessoes_recebidas.csv

**Descrição:** Resseguro: Movimentação por Cessionária

| Campo | Descrição |
|---|---|
| `coenti` | Código da entidade cessionária |
| `damesano` | Período (Ano/Mês) a que se referem os dados |
| `tipo_cessao` | Tipo da cessão: `resseguro` (quadro 51) ou `retrocessão` (quadro 51R) |
| `grupo` | Grupamento de ramos, conforme Circular SUSEP nº 535/2016 |
| `cessao` | Valor da conta "Cessões", segregado por cessionária, ano/mês e grupo de ramos |
| `recuperacao` | Valor da conta "Recuperações", segregado por cessionária, ano/mês e grupo de ramos |
| `comissao` | Valor da conta "Comissão", segregado por cessionária, ano/mês e grupo de ramos |
| `lucro` | Valor da conta "Lucro", segregado por cessionária, ano/mês e grupo de ramos |
| `corretagem` | Valor da conta "Corretagem", segregado por cessionária, ano/mês e grupo de ramos |
| `outros` | Valor da conta "Outros", segregado por cessionária, ano/mês e grupo de ramos |

---

## Ses_cias.csv

**Descrição:** Cias do Mercado — cadastro de empresas supervisionadas.

| Campo | Descrição |
|---|---|
| `Coenti` | Código da Empresa |
| `Noenti` | Nome da Empresa |
| `Cogrupo` | Código do grupo econômico *(informação ainda não disponível)* |
| `Nogrupo` | Nome do grupo econômico *(informação ainda não disponível)* |

---

## Ses_Contrib_Benef.csv

**Descrição:** Valores de contribuições e benefícios (previdência).

| Campo | Descrição |
|---|---|
| `damesano` | Ano e mês da informação |
| `coenti` | Código da Empresa |
| `tipoProd` | Tipo de produto |
| `contrib` | Total de contribuições |
| `benef` | Total de benefícios |

---

## Ses_pl_margem.csv

**Descrição:** Patrimônio Líquido e Margem de Solvência

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| `plajustado` | Patrimônio Líquido Ajustado |
| `margem` | Margem de Solvência |

---

## ses_prev_trad_resgates.csv

**Descrição:** Previdência Tradicional — Resgates

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| *(demais campos de resgates de previdência tradicional)* | — |

---

## SES_prov_segprev.csv

**Descrição:** Seguradoras: Provisão das Operações de Previdência

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| `valor` | Total das Provisões Técnicas |

---

## Ses_ramos.csv

**Descrição:** Tabela de referência — Ramos de seguros.

| Campo | Descrição |
|---|---|
| `coramo` | Código do Grupo/Ramo no FIP |
| `noramo` | Nome do Ramo |

---

## SES_Balanco.csv

**Descrição:** Valores de balanço e demonstração. Utilizar em conjunto com a tabela `Ses_campos`, associando `CMPID` (SES_Balanco) com `NUITEM` (Ses_campos).

| Campo | Descrição |
|---|---|
| `COENTI` | Código da Empresa |
| `DAMESANO` | Ano e mês da informação |
| `CMPID` | Código do campo (join com `nuitem` de Ses_campos) |
| `VALOR` | Valor da conta contábil |

---

## ses_cap_uf.csv

**Descrição:** Capitalização — Dados por UF

| Campo | Descrição |
|---|---|
| `COENTI` | Código da Empresa |
| `DAMESANO` | Ano e mês da informação |
| `UF` | Unidade Federativa |
| `PREMIO` | Prêmios (R$) |
| `RESGPAGO` | Resgates Pagos (R$) |
| `SORTPAGO` | Sorteios Pagos (R$) |
| `NUMPARTIC` | Média de Participantes no Período |
| `RESGATANTES` | Resgatantes |

---

## ses_contatos.csv

**Descrição:** Contatos das entidades supervisionadas.

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| *(demais campos de contato)* | — |

---

## ses_gruposramos.csv

**Descrição:** Tabela de referência — Grupos de Ramos, conforme **Circular SUSEP nº 535/2016**.

| Campo | Descrição |
|---|---|
| `GRACODIGO` | Código do grupamento de ramos |
| `GRANOME` | Nome do Grupamento de ramos |

---

## ses_pgbl_contrib.csv

**Descrição:** PGBL — Contribuições

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| *(demais campos de contribuições PGBL)* | — |

---

## ses_pgbl_fundos.csv

**Descrição:** PGBL — Fundos

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| *(demais campos de fundos PGBL)* | — |

---

## ses_pgbl_resgates.csv

**Descrição:** PGBL — Resgates

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| *(demais campos de resgates PGBL)* | — |

---

## ses_pgbl_uf.csv

**Descrição:** PGBL — Dados por Unidade Federativa

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| `UF` | Unidade Federativa |
| *(demais campos)* | — |

---

## ses_prev_cap_uf.csv

**Descrição:** Previdência Capitalização — Dados por UF

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| `UF` | Unidade Federativa |
| *(demais campos)* | — |

---

## ses_prev_uf.csv

**Descrição:** Previdência — Dados por Unidade Federativa

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| `UF` | Unidade Federativa |
| *(demais campos)* | — |

---

## ses_provramos.csv

**Descrição:** Seguradoras: Provisão por Ramo

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| `coramo` | Código do Ramo no FIP |
| *(demais campos de provisão)* | — |

---

## ses_quantcap.csv

**Descrição:** Capitalização — Quantitativos (número de títulos, participantes etc.)

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| *(demais campos quantitativos)* | — |

---

## ses_quantprev_benef.csv

**Descrição:** Previdência — Quantitativo de Beneficiários

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| *(demais campos de contagem de beneficiários)* | — |

---

## ses_quantprev_part.csv

**Descrição:** Previdência — Quantitativo de Participantes

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| *(demais campos de contagem de participantes)* | — |

---

## ses_transferenciasexternas.csv

**Descrição:** Transferências Externas (portabilidade entre entidades)

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| *(demais campos de transferências)* | — |

---

## SES_UF2.csv

**Descrição:** Seguros: Prêmios e Sinistros por Unidade Federativa

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| `ramos` | Código do Ramo |
| `UF` | Unidade Federativa |
| `gracodigo` | Código do grupamento de ramos |
| `premio_dir` | Prêmios Diretos |
| `premio_ret` | Prêmios Retidos |
| `prem_ret_liq` | Prêmios Retidos Líquidos |
| `sin_dir` | Sinistros Diretos |
| `salvados` | Salvados de sinistros |
| `recuperacao` | Recuperações |

---

## SES_VALORESRESMOVGRUPOS.csv

**Descrição:** Resseguros: Prêmios Ganhos e Sinistros Retidos, segregados por grupamento de ramos.

> Utilizar em conjunto com `Ses_campos`, associando `CMPID` (SES_VALORESRESMOVGRUPOS) com `NUITEM` (Ses_campos).

| Campo | Descrição |
|---|---|
| `COENTI` | Código da Empresa |
| `DAMESANO` | Ano e mês da informação |
| `CMPID` | Código do campo (join com `nuitem` de Ses_campos) |
| `GRACODIGO` | Código do grupamento de ramos |
| `VALOR` | Valor |
| `ID` | Identificador |

---

## Ses_vgbl_fundos.csv

**Descrição:** VGBL — Provisão Matemática de Benefícios a Conceder (Fundos)

| Campo | Descrição |
|---|---|
| `coenti` | Código da Empresa |
| `damesano` | Ano e mês da informação |
| *(demais campos de fundos VGBL)* | — |

---

## SES_ValoresMovRamos.csv

**Descrição:** Mapas Demonstrativos de Prêmios, Sinistros e Custos de Aquisição, por ramo de seguro.

> Utilizar em conjunto com `Ses_campos`, associando `CMPID` (SES_ValoresMovRamos) com `NUITEM` (Ses_campos).

| Campo | Descrição |
|---|---|
| `COENTI` | Código da Empresa |
| `DAMESANO` | Ano e mês da informação |
| `CMPID` | Código do campo (join com `nuitem` de Ses_campos) |
| `RAMCODIGO` | Código do ramo de seguro |
| `GRACODIGO` | Código do grupamento de ramos |
| `VALOR` | Valor da conta |
| `SEQ` | Identificador da posição do campo no respectivo mapa demonstrativo |
| `QUADRO` | Identificação do quadro do FIP a que pertence o campo |

### Principais campos disponíveis via `Ses_campos` (join por `CMPID`)

| Campo (CMPID) | Descrição |
|---|---|
| `mraPremiosContaRetDireta` | Prêmios — Conta Retenção Direta |
| `mraPremiosContaCossAceito` | Prêmios — Conta Cosseguro Aceito |
| `mraPremiosContaCossCedido` | Prêmios — Conta Cosseguro Cedido |
| `mraPremiosContaRessCedido` | Prêmios — Conta Resseguro Cedido |
| `mraPremiosContaRetLiquida` | Prêmios — Conta Retenção Líquida |
| `mraPremiosContaVarProv` | Prêmios — Variação de Provisão |
| `mraPremiosContaRetrAceita` | Prêmios — Conta Retrocessão Aceita |
| `mraPremiosCintaPremGanho` | Prêmios Ganhos |
| `MRAprememitrvne` | Total de prêmios estimados dos riscos vigentes mas não emitidos no mês de referência |
| `MRAPREMEMITCONSORCIOSFUNDOS` | Total do valor da conta "Consórcios e Fundos" no mês de referência |
| `MRASINRETVARSINRET` | Despesas com Benefícios + Variação do sinistro retido no mês de referência |
| `MRASINRETSEGURO` | Sinistros avisados/despesas (administrativos e judiciais) no mês, relativos a operações de seguro direto |
| `MRASINRETTOTAL` | Somatório: Retenção Líquida Direta + Retrocessões Aceitas + Variação da Prov. IBNR + Serviços de Assistência, líquido de Salvados e Ressarcidos de Retrocessão Aceita |
| `MRASINRETTOTALESTRANG` | Sinistros totais (estrangeiro) |
| `MRASINRETVARIBNR` | Variação da provisão de IBNR entre o mês de referência e o mês imediatamente anterior |

---

## Ses_RMovRam.csv

> **⚠️ Tabela descontinuada desde 2014.**

**Descrição (histórica):** Movimentação por Ramo — dados de prêmios estimados e sinistros retidos.

| Campo | Descrição |
|---|---|
| `MRASINRETSEGURO` | Sinistros avisados/despesas no mês de referência, relativos a operações de seguro direto |
| `MRAprememitrvne` | Total de prêmios estimados dos riscos vigentes mas não emitidos no mês de referência |
| `MRASINRETTOTAL` | Somatório dos valores de sinistro retido |
| `MRASINRETTOTALESTRANG` | Sinistros totais (estrangeiro) |
| `MRASINRETVARIBNR` | Variação da provisão de IBNR |
| *(demais campos MRA...)* | — |

---

## Ses_seguros.csv

**Descrição:** Seguros: Prêmios e Sinistros — tabela principal de prêmios por ramo de seguro.

| Campo | Descrição |
|---|---|
| `damesano` | Ano e mês da informação |
| `coenti` | Código da Empresa |
| `cogrupo` | Código do grupo (grupamento de ramos) |
| `coramo` | Código do Ramo no FIP |
| `premio_direto` | Prêmio Direto (R$) |
| `premio_de_seguros` | Prêmio de Seguros (R$) |
| `premio_retido` | Prêmio Retido (R$) |
| `premio_ganho` | Prêmio Ganho (R$) |
| `sinistro_direto` | Sinistro de Seguros (R$) |

---

## Relacionamentos entre tabelas

```
Ses_cias ─────────────────────────────── coenti ─────── LimiteRetProxVig
                                                         Ses_seguros
                                                         SES_UF2
                                                         SES_ValoresMovRamos
                                                         SES_VALORESRESMOVGRUPOS
                                                         ses_provramos
                                                         ses_cap_uf
                                                         Ses_pl_margem
                                                         SES_Balanco
                                                         ...

Ses_ramos ────────────────────────────── coramo ──────── Ses_seguros
                                                         ses_provramos
                                                         LimiteRetProxVig
                                                         SES_ValoresMovRamos (RAMCODIGO)
                                                         SES_UF2 (ramos)

ses_gruposramos ──────────────────────── GRACODIGO ───── SES_UF2 (gracodigo)
                                                         SES_ValoresMovRamos (GRACODIGO)
                                                         SES_VALORESRESMOVGRUPOS (GRACODIGO)
                                                         Ses_cessoes_recebidas (grupo)

Ses_campos ───────────────────────────── nuitem ──────── SES_ValoresMovRamos (CMPID)
                                                         SES_VALORESRESMOVGRUPOS (CMPID)
                                                         SES_Balanco (CMPID)
```

---

## Tabelas com dados de prêmio por linha de negócio

| Tabela | Granularidade | Métricas de Prêmio |
|---|---|---|
| **Ses_seguros.csv** | Empresa × Ramo × Mês | Direto, Seguros, Retido, Ganho |
| **SES_UF2.csv** | Empresa × Ramo × UF × Mês | Direto, Retido, Retido Líquido |
| **SES_ValoresMovRamos.csv** | Empresa × Ramo × Grupamento × Campo × Mês | Múltiplos (via Ses_campos) |
| **SES_VALORESRESMOVGRUPOS.csv** | Empresa × Grupamento × Campo × Mês | Prêmios Ganhos (resseguro) |

> Para decodificar ramos em nomes: join `coramo` → `Ses_ramos.noramo`  
> Para decodificar grupamentos em nomes: join `GRACODIGO` → `ses_gruposramos.GRANOME`
