# Escopo de Ramos e Grupos de Ramos — Análise de Mercado Youse

> Documento de referência para a seleção de ramos e grupos de ramos utilizados na análise de market sizing da Youse.  
> Base de dados: SUSEP/SES (formato CSV, a partir de abr/2013).

---

## Critérios de seleção

1. **Aderência ao portfólio:** apenas ramos que compõem ou são diretamente comparáveis aos 4 produtos da Youse.
2. **Ramos ativos:** ramos com `(RUN OFF)` no nome foram excluídos — representam carteiras encerradas, sem novos negócios. Sua inclusão distorceria métricas de mercado atual.
3. **Relação grupo ↔ ramo:** os 2 primeiros dígitos do código `coramo` determinam o `gracodigo` (validado em 100% das ~10 milhões de linhas de `SES_UF2`).

---

## Produtos Youse e mapeamento SUSEP

### Seguro Auto + Seguro Auto por Km
**Grupo:** `05 - Automóvel` (`gracodigo = 5`)

> O seguro auto por km não possui ramo próprio na SUSEP. É comercializado sob os mesmos ramos do auto convencional (`0531` + `0553`), diferindo apenas na modalidade de precificação.

| coramo | Nome do Ramo | Relevância |
|---|---|---|
| `0531` | Automóvel - Casco | **Principal** — cobertura de danos ao veículo (colisão, incêndio, roubo/furto) |
| `0553` | R. C. Facultativa Veículos - RCFV | **Principal** — cobertura de responsabilidade civil ao terceiro |
| `0542` | Assistência e Outras Coberturas - Auto | Complementar — assistência 24h, chaveiro, guincho, carro reserva |
| `0520` | Acidentes Pessoais Passageiros - APP | Complementar — cobertura de morte e invalidez de ocupantes |
| `0525` | Carta Verde | Periférico — RC obrigatória para veículos em países do MERCOSUL |
| `0527` | RC Veic Pass Acordos fora Mercosul | Periférico — RC obrigatória para viagens internacionais |

**Ramos excluídos (com justificativa):**

| coramo | Nome | Motivo da exclusão |
|---|---|---|
| `0523` | RC T.ROD.PAS INTEST OU INT (RUN OFF) | Descontinuado |
| `0524` | Garantia Est./Ext. Garantia Auto | Produto bancário/dealer, não seguradora direta |
| `0526` | Seguro Popular de Auto Us (RUN OFF) | Descontinuado |
| `0544` | R.C.T.Viag InterPes Tran/ñ (RUN OFF) | Descontinuado |
| `0583` | DPVAT Extinto | Extinção do DPVAT em 2020 |
| `0588` | DPVAT | Extinto — apenas histórico |
| `0589` | DPVAT (RUN OFF) | Descontinuado |

---

### Seguro Residencial (Reside)
**Grupo:** `01 - Patrimonial` (`gracodigo = 1`)

> **Atenção:** seguro residencial ≠ seguro habitacional.  
> O grupo `10 - Habitacional` cobre produtos atrelados a financiamento imobiliário (MIP/DFI — Caixa, bancos), vendidos obrigatoriamente junto com o financiamento. O produto Youse Reside é um seguro compreensivo residencial de livre contratação, classificado em `01 - Patrimonial`.

| coramo | Nome do Ramo | Relevância |
|---|---|---|
| `0114` | Compreensivo Residencial | **Principal** — produto direto Youse Reside |
| `0116` | Compreensivo Condomínio | Complementar — cobertura de áreas comuns |
| `0112` | Assistência - Bens em Geral | Complementar — assistência residencial |
| `0113` | Vidros | Complementar — cobertura de vidros e espelhos |

**Ramos excluídos (com justificativa):**

| coramo | Nome | Motivo da exclusão |
|---|---|---|
| `0111` | Incêndio Tradicional (RUN OFF) | Descontinuado — substituído pelo compreensivo |
| `0115` | Roubo (RUN OFF) | Descontinuado |
| `0117` | Tumultos | Produto corporativo/grandes riscos |
| `0118` | Compreensivo Empresarial | Produto empresarial — fora do foco B2C |
| `0141` | Lucros Cessantes | Produto empresarial |
| `0142` | Lucros Cessantes Cobertura Simples | Produto empresarial |
| `0143` | Fidelidade | Produto empresarial/RH |
| `0167` | Riscos de Engenharia | Produto de construção civil |
| `0171` | Riscos Diversos | Produto industrial |
| `0173` | Global de Bancos | Produto bancário |
| `0176` | Riscos Diversos - Planos Conjugados | Produto empresarial |
| `0195` | Garantia Est./Ext.Gar - Bens em Geral | Produto bancário |
| `0196` | Riscos Nomeados e Operacionais | Produto de grandes riscos |

---

### Seguro Vida
**Grupo:** `13 - Pessoas Individual` (`gracodigo = 13`)

> A Youse comercializa seguros de vida para pessoa física de forma individual (canal digital direto). Por isso, o foco está no grupo `13 - Pessoas Individual`.  
> O grupo `09 - Pessoas Coletivo` foi excluído pois concentra produtos vendidos em massa via RH/empresas (apólices coletivas), que não é o modelo de negócio da Youse.  
> **Nota sobre a classificação SUSEP:** historicamente, muitos produtos individuais foram registrados com código `09xx` (RUN OFF). Os equivalentes ativos migraram para `13xx`.

| coramo | Nome do Ramo | Relevância |
|---|---|---|
| `1391` | Vida | **Principal** — seguro de vida individual |
| `1396` | Seguro de Vida Universal | **Principal** — vida com componente de acumulação |
| `1381` | Acidentes Pessoais | Complementar — morte e invalidez por acidente |
| `1384` | Doenças Graves ou Doença Terminal | Complementar — cobertura de doenças críticas |
| `1387` | Desemprego/Perda de Renda | Complementar |
| `1390` | Eventos Aleatórios | Complementar |

**Ramos excluídos (com justificativa):**

| coramo | Nome | Motivo da exclusão |
|---|---|---|
| `1329` | Funeral | Produto de nicho, não ofertado pela Youse |
| `1336` | Perda Certif. Habilit. de Vôo-PCHV | Produto de nicho (aviadores) |
| `1369` | Viagem | Produto pontual/não recorrente |
| `1377` | Prestamista | Produto bancário atrelado a crédito |
| `1380` | Educacional | Produto bancário/escola |
| `1383` | Dotal Misto | Produto de poupança/previdência |
| `1386` | Dotal Puro | Produto de poupança/previdência |
| `1392` | VGBL/VAGP/VRGP/VRSA/VRID/VDR | Produto de previdência/acumulação — não é seguro de vida |

---

## Grupos excluídos (com justificativa)

| gracodigo | Nome do Grupo | Motivo da exclusão |
|---|---|---|
| `02` | Riscos Especiais | Petróleo/Nuclear/Satélites em RUN OFF — sem relação com a Youse |
| `03` | Responsabilidades | D&O, RC Ambiental, RC Profissional — corporativo, não B2C |
| `04` | Cascos | Cascos de embarcações e aeronaves — não veículos de passeio |
| `06` | Transportes | Seguro de carga/mercadorias — B2B, sem relação com auto pessoa física |
| `07` | Riscos Financeiros | Garantias, fiança locatícia, stop loss — corporativo |
| `08` | Crédito | Seguro de crédito — corporativo/bancário |
| `09` | Pessoas Coletivo | Produtos coletivos/RH — modelo de distribuição diferente da Youse |
| `10` | Habitacional | Seguro habitacional atrelado a financiamento imobiliário (SFH/SFI) |
| `11` | Rural | Seguro agrícola/pecuário — sem relação com a Youse |
| `12` | Outros | Saúde Individual/Grupal — operadoras de saúde, não seguradoras diretas |
| `14` | Marítimos | Embarcações — sem relação com a Youse |
| `15` | Aeronáuticos | Aviação — sem relação com a Youse |
| `16` | Microsseguros | Produtos de baixo ticket — segmento distinto do portfólio Youse |
| `17` | Petróleo | Riscos de petróleo — corporativo/industrial |
| `18` | Nucleares | Riscos nucleares — sem relação com a Youse |
| `19` | Saúde | Apenas resseguros de saúde (1985) — não operações diretas |
| `20` | Aceitações do Exterior | Operações internacionais |
| `21` | Sucursal no Exterior | Operações internacionais |
| `22` | Pessoas EFPC | Fundos de pensão — modelo regulatório diferente |

---

## Resumo para uso em código

```python
GRACODIGOS_YOUSE = {
    "auto":        5,
    "residencial": 1,
    "vida":        13,
}

RAMOS_YOUSE = {
    "auto":        [531, 553, 542, 520, 525, 527],
    "residencial": [114, 116, 112, 113],
    "vida":        [1391, 1396, 1381, 1384, 1387, 1390],
}

# De/para: ramo → produto
PRODUTO_POR_RAMO = {
    ramo: produto
    for produto, ramos in RAMOS_YOUSE.items()
    for ramo in ramos
}
```

> Os valores acima usam o tipo inteiro, pois `SES_UF2.csv` armazena `ramos` e `gracodigo` como inteiros (ex.: `"0531"` → `531`).
