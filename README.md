# 🐧 Imputação de Dados no Dataset Penguins (Palmer Penguins)

Projeto desenvolvido para a disciplina **Mineração e Visualização de Dados** (PUC-Campinas), com o objetivo de **corrigir (imputar) valores ausentes** no dataset Palmer Penguins e **comparar a distribuição dos dados antes e depois** das correções por meio de **dashboards no Power BI** e processamento/documentação em **Python (Jupyter Notebook)**. :contentReference[oaicite:1]{index=1}

## 🎯 Enunciado (resumo)
**Corrigir a base de dados Penguins** disponibilizada no notebook, mostrando a distribuição dos dados **antes e depois** das correções.  
Trabalho em grupo (4 alunos) e avaliação em aula após arguição. :contentReference[oaicite:2]{index=2}

### Critérios/Tópicos avaliados
- Dashboard com os dados da base inicial (1pt)
- Imputar colunas numéricas (1pt)
- Justificativas colunas numéricas (4pts)
- Imputar colunas categóricas (1pt)
- Justificativas colunas categóricas (2pts)
- Dashboard com dados da base imputada (1pt)
> Dashboards em **Power BI** e processamento/discussão em **Python Notebook**, com etapas anotadas e avaliação do processo de imputação. :contentReference[oaicite:3]{index=3}

---

## 👥 Grupo
Trabalho em grupo (conjunto “Imputando”) com **4 integrantes**. :contentReference[oaicite:4]{index=4}

---

## 🧠 Dataset
Fonte do dataset (Kaggle):
https://www.kaggle.com/code/parulpandey/penguin-dataset-the-new-iris

O conjunto contém características morfológicas de pinguins (ex.: medidas do bico, nadadeira e massa corporal), com variáveis categóricas como **species**, **island** e **sex**. :contentReference[oaicite:5]{index=5}

---

## 📁 Arquivos do repositório
- `Penguins - Imputação de Dados - Jupyther Notebook.ipynb`  
  Notebook com EDA, imputações, justificativas e avaliação das distribuições (antes vs depois). :contentReference[oaicite:6]{index=6}
- `Penguins_Dashboard_BI.pbix`  
  Dashboard no Power BI (base original + base imputada). :contentReference[oaicite:7]{index=7}
- `Penguins_Dashboard_BI_pdf.pdf`  
  Exportação do dashboard para PDF (visão rápida). :contentReference[oaicite:8]{index=8}
- `Penguins Dataset - Relatório Final.pdf`  
  Relatório com metodologia, justificativas e conclusões. :contentReference[oaicite:9]{index=9}

---

## ✅ O que foi implementado (mapeado ao enunciado)

### 1) Dashboard com os dados da base inicial (ANTES)
Foram criados dashboards em Power BI a partir da base com valores ausentes, evidenciando categorias como “em branco” e “ilha desconhecida”, e o impacto dos NaNs nas análises por espécie/ilha/sexo. :contentReference[oaicite:10]{index=10}

**Principais visuais (antes):**
- Massa corporal média e tamanho médio da asa (antes) :contentReference[oaicite:11]{index=11}
- Comprimento médio do bico e profundidade média do bico (antes) :contentReference[oaicite:12]{index=12}
(Preview em PDF: páginas com “Dados Ausentes”). :contentReference[oaicite:13]{index=13}

---

### 2) Imputação de colunas numéricas + justificativas
**Colunas numéricas tratadas:** `bill_length_mm`, `bill_depth_mm`, `flipper_length_mm`, `body_mass_g`. :contentReference[oaicite:14]{index=14}

**Técnica escolhida:** **KNN Imputer (K=5, weights='distance')**, por utilizar registros semelhantes (“vizinhos”) ao invés de um valor global (como média/mediana), reduzindo distorções e respeitando o contexto local dos dados. :contentReference[oaicite:15]{index=15}

**Pré-processamento:** normalização com **MinMaxScaler** (0 a 1), necessária porque o KNN usa distância e as variáveis estão em escalas diferentes (gramas vs milímetros). Depois, foi feita a desnormalização para retornar às unidades originais. :contentReference[oaicite:16]{index=16}

**Avaliação:** comparação visual das distribuições antes/depois indicou preservação do formato geral e melhora na consistência, com curvas mais simétricas e menos “picos” artificiais. :contentReference[oaicite:17]{index=17}

---

### 3) Imputação de colunas categóricas + justificativas
**Colunas categóricas tratadas:** `species`, `island`, `sex`. :contentReference[oaicite:18]{index=18}

**Para `species` e `island`:** método **Forward Fill (ffill)**, escolhido porque havia organização sequencial em blocos (linhas seguidas com mesma espécie/ilha). Isso evita imputações aleatórias e mantém coerência local. :contentReference[oaicite:19]{index=19}

**Para `sex`:** imputação por **característica morfológica**, relacionando `sex` com `bill_depth_mm` **dentro de cada espécie**, usando **medianas** (mais robustas a outliers) e atribuindo o sexo cuja mediana estivesse mais próxima do valor do registro. :contentReference[oaicite:20]{index=20}

---

### 4) Dashboard com os dados imputados (DEPOIS)
Após a imputação, os dashboards passaram a exibir análises mais completas, sem categorias “em branco/desconhecido”, permitindo comparações mais confiáveis entre espécie/ilha/sexo. :contentReference[oaicite:21]{index=21}

No dashboard imputado, por exemplo, destacam-se padrões como:
- Gentoo machos de Biscoe com maior massa corporal média. 
- Biscoe com maiores médias de nadadeira em vários grupos. :contentReference[oaicite:23]{index=23}

(Preview em PDF: páginas com “Dados Imputados”). :contentReference[oaicite:24]{index=24}

---

## 🛠 Tecnologias utilizadas
- **Python (Jupyter Notebook)**: pandas, numpy, scikit-learn (KNNImputer, MinMaxScaler) :contentReference[oaicite:25]{index=25}
- **Power BI**: dashboards antes/depois para comparação das distribuições 

---

## 🧾 Como abrir o projeto
1. Abra o notebook:
   - `Penguins - Imputação de Dados - Jupyther Notebook.ipynb`
2. Abra o dashboard no Power BI Desktop:
   - `Penguins_Dashboard_BI.pbix`
3. Para visualizar rapidamente sem Power BI:
   - `Penguins_Dashboard_BI_pdf.pdf`
4. Consulte o relatório final (metodologia e justificativas):
   - `Penguins Dataset - Relatório Final.pdf`

---

## 📌 Conclusão (resumo)
O projeto demonstrou a importância de tratar dados ausentes com técnicas apropriadas e justificadas. O uso de **KNN** (com normalização) preservou padrões relevantes nas variáveis numéricas, enquanto **ffill** e imputação por **características morfológicas** mantiveram coerência nas variáveis categóricas. Os dashboards finais ficaram mais completos e confiáveis para análise. :contentReference[oaicite:27]{index=27}
