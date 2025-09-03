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
Guia + Gantt + Contagem + Mapa
<img width="1500" height="660" alt="Captura de tela 2025-09-03 151908" src="https://github.com/user-attachments/assets/754688e1-4d19-415f-b8f1-79fc51435848" />


**O que mostra**
- **Guia de uso** explicando o *slicer de métricas* que sincroniza os visuais.
- **Cronograma (Gantt)**: barras entre **Data de Início** e **Data de Término**; **cores por gerente**.
- **Bar chart**: **Quantidade de projetos por gerente**.
- **Mapa de bolhas**: pontos de entrega; **tamanho da bolha = nº de projetos** na região.

**Leitura rápida**  
Use o *slicer “Métricas”* para trocar o indicador analisado em todos os visuais da página.

---

## 2) Métrica selecionada: Orçamento solicitado por Gerente
Orçamento solicitado por Gerente
<img width="1487" height="651" alt="Captura de tela 2025-09-03 151926" src="https://github.com/user-attachments/assets/1434e6c1-48f7-4c40-9a99-c094f8c2cb29" />


**O que mostra**
- O *slicer “Métricas”* (setas vermelhas) está em **“Valor do orçamento solicitado aos clientes”**.  
- **Ranking por gerente** com o total solicitado (ex.: Luis e Bianca lideram no print).

**Leitura rápida**  
Concentração de **pipeline** por gerente → direciona atenção comercial e capacidade da equipe.

---

## 3) Gestão Operacional/Estratégica – KPIs + Workload por Gerente
Gestão Operacional/Estratégica
<img width="859" height="796" alt="Captura de tela 2025-09-03 152020" src="https://github.com/user-attachments/assets/3df8d175-b61c-49e8-9d50-6508fda74e3d" />

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
Projeção de HC por cargo
<img width="851" height="786" alt="Captura de tela 2025-09-03 152038" src="https://github.com/user-attachments/assets/53d10736-27a3-417e-aba3-20bc91755fa5" />


**O que mostra**
- **Cards** de **Lucro Líquido** e **%Margem** do portfólio.
- Quatro gráficos (**Coordenador, Sênior, Pleno, Júnior**) com a **curva de colaboradores necessários**.
- **Linha pontilhada = média**; tooltip traz **HC médio**, **custos/mês (22d)** e **custo total** por cargo.

**Leitura rápida**  
Base para **planejamento de rampa/downsizing** por role e para decisões de contratação.

---

## 5) Plano de Contratação – Coordenadores (tabela + gráfico)
Projeção tabular e gráfica – Coordenadores
<img width="1438" height="788" alt="Captura de tela 2025-09-03 152104" src="https://github.com/user-attachments/assets/f940c605-02e8-48af-b7a8-12adeeba41e6" />


**O que mostra**
- **Tabela temporal** de **Ações** (+1 contratar / −1 desligar).
- **Gráfico** compara **horas dos projetos ativos** × **colaboradores necessários**.

**Leitura rápida**  
Transforma demanda de horas em **plano operacional** (datas e quantidade de movimentações).

---

## 6) Catálogo de Medidas (DAX) + HTML Inline
Medidas e expressão DAX/HTML
<img width="1077" height="792" alt="Captura de tela 2025-09-03 152141" src="https://github.com/user-attachments/assets/4bb468ae-c6be-4efa-91f0-8a1d77d08968" />


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
Relacionamentos do modelo
<img width="1074" height="785" alt="Captura de tela 2025-09-03 152157" src="https://github.com/user-attachments/assets/b4a1ed98-95db-4aec-b194-a109985cf39b" />


**O que mostra**
- Relações entre **Equipe**, **Cronograma** e **Orçamento**, e as **LocalDateTables** (Início/Término).
- **Cross-filter** majoritariamente **BothDirections**; **OneDirection** nas pontes de datas.

**Leitura rápida**  
Modelo otimizado para análises por **janelas de início/fim**, suportando Gantt, workload e KPIs de prazo de contratação.

---

> **Nota**: os valores exibidos nos prints são ilustrativos do cenário capturado.
>
> 
