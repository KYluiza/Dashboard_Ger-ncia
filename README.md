# Case Sonar — Resumo do Desafio (o que foi solicitado)

## 🎯 Objetivo
Criar, no **Power BI**, um **dashboard interativo** para analisar a carteira de projetos com foco em **faturamento, custos, rentabilidade e prazos**.

## 🧩 Cenário
- **Personagem:** Roberto Silva, Gerente de Projetos Sênior.  
- **Estrutura:** 5 gerentes subordinados que coordenam equipes e asseguram entregas no prazo e com qualidade.

## 💸 Política de Preços (Rate Card)
Aplicável a todos os projetos/clientes; **receita** e **custo por hora** variam conforme o cargo:

| Cargo                  | Valor cobrado (R$/h) | Valor pago (R$/h) |
|------------------------|----------------------|-------------------|
| Gerente do Projeto     | 100                  | 100               |
| Coordenador            | 40                   | 30                |
| Profissional Sênior    | 20                   | 18                |
| Profissional Pleno     | 18                   | 16                |
| Profissional Júnior    | 12                   | 14                |

## 📦 Entregável
Um **dashboard** que permita uma análise completa da **carteira de projetos de Roberto**, com liberdade para definir a melhor apresentação das informações.

## 📊 Indicadores-chave esperados
- **Faturamento** *(receita por horas faturáveis × preço do cargo)*

Custos (todas as horas × custo do cargo)

Rentabilidade (margem R$ e %)


Observação: a tabela de preços traz diferenças por cargo, influenciando diretamente blended rate, margem por projeto e unit economics (ex.: Júnior tem preço < custo).

## 1) Guia + Cronograma (Gantt) + Quantidade + Mapa
![Guia + Gantt + Contagem + Mapa]

**O que mostra**
- **Guia de uso** explicando o *slicer de métricas* que sincroniza os visuais.
- **Cronograma (Gantt)**: barras entre **Data de Início** e **Data de Término**; **cores por gerente**.
- **Bar chart**: **Quantidade de projetos por gerente**.
- **Mapa de bolhas**: pontos de entrega; **tamanho da bolha = nº de projetos** na região.

**Leitura rápida**  
Use o *slicer “Métricas”* para trocar o indicador analisado em todos os visuais da página.

---

## 2) Métrica selecionada: Orçamento solicitado por Gerente
![Orçamento solicitado por Gerente]

**O que mostra**
- O *slicer “Métricas”* (setas vermelhas) está em **“Valor do orçamento solicitado aos clientes”**.  
- **Ranking por gerente** com o total solicitado (ex.: Luis e Bianca lideram no print).

**Leitura rápida**  
Concentração de **pipeline** por gerente → direciona atenção comercial e capacidade da equipe.

---

## 3) Gestão Operacional/Estratégica – KPIs + Workload por Gerente
![Gestão Operacional/Estratégica]
**O que mostra**
- **Cards**: **% Margem de lucro** (ex.: 9,30%), **Total de projetos ativos** (ex.: 41) e **Gerente Top Margem**.
- **Sparklines** por gerente (% de lucro ao longo do tempo).
- **Tabela de KPIs** por gerente: **Lucro Líquido**, **Projetos Ativos**, **Workload (%)**, **Orçamento**, **Valor pago à equipe**.
- **Alertas de workload**:  
  - **>10 projetos** → ❗ (vermelho)  
  - **6–10** → ⚠️ (laranja)  
  - **≤5** → dentro da meta

**Leitura rápida**  
Equilibra **resultado** (margem) com **capacidade** (workload), destacando onde redistribuir esforço.

---

## 4) Projeção de Headcount (por cargo)
![Projeção de HC por cargo]

**O que mostra**
- **Cards** de **Lucro Líquido** e **%Margem** do portfólio.
- Quatro gráficos (**Coordenador, Sênior, Pleno, Júnior**) com a **curva de colaboradores necessários**.
- **Linha pontilhada = média**; tooltip traz **HC médio**, **custos/mês (22d)** e **custo total** por cargo.

**Leitura rápida**  
Base para **planejamento de rampa/downsizing** por role e para decisões de contratação.

---

## 5) Plano de Contratação – Coordenadores (tabela + gráfico)
![Projeção tabular e gráfica – Coordenadores]

**O que mostra**
- **Tabela temporal** de **Ações** (+1 contratar / −1 desligar).
- **Gráfico** compara **horas dos projetos ativos** × **colaboradores necessários**.

**Leitura rápida**  
Transforma demanda de horas em **plano operacional** (datas e quantidade de movimentações).

---

## 6) Catálogo de Medidas (DAX) + HTML Inline
![Medidas e expressão DAX/HTML]
**O que mostra**
- Lista de **measures** com **Name** e **Description** (ex.: `#Lucro Líquido`, `#soma de projetos`).
- **Expression** da `_TabelaProjetosHTML`: gera **tabela HTML** com KPIs e **alertas**:
  - **>10 projetos** → ❗ vermelho  
  - **6–10** → ⚠️ laranja  
  - **Workload = 0** → “– –”

**Leitura rápida**  
Documentação **no próprio PBIX**, com **HTML inline** para storytelling (cores, ícones, badges).

---

## 7) Modelo de Dados – Relacionamentos
![Relacionamentos do modelo]

**O que mostra**
- Relações entre **Equipe**, **Cronograma** e **Orçamento**, e as **LocalDateTables** (Início/Término).
- **Cross-filter** majoritariamente **BothDirections**; **OneDirection** nas pontes de datas.

**Leitura rápida**  
Modelo otimizado para análises por **janelas de início/fim**, suportando Gantt, workload e KPIs de prazo.

---

> **Nota**: os valores exibidos nos prints são ilustrativos do cenário capturado.
