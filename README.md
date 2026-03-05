# Imputação de Dados no Dataset Penguins (Palmer Penguins)

Projeto desenvolvido para a disciplina **Mineração e Visualização de Dados** (PUC-Campinas), com o objetivo de **corrigir (imputar) valores ausentes** no dataset Palmer Penguins e **comparar a distribuição dos dados antes e depois** das correções por meio de **dashboards no Power BI** e processamento/documentação em **Python (Jupyter Notebook)**.

<p align="center">
  <img src="/read-me-img/penguins.png" width="700">
</p>

## 🎯 Enunciado (resumo)
**Corrigir a base de dados Penguins** disponibilizada no notebook, mostrando a distribuição dos dados **antes e depois** das correções.  
Trabalho em grupo (4 alunos) e avaliação em aula após arguição. 

---

## 🧠 Dataset
Fonte do dataset (Kaggle):
https://www.kaggle.com/code/parulpandey/penguin-dataset-the-new-iris

O conjunto contém características morfológicas de pinguins (ex.: medidas do bico, nadadeira e massa corporal), com variáveis categóricas como **species**, **island** e **sex**. 

---

## 📁 Arquivos do repositório
- `Penguins - Imputação de Dados - Jupyther Notebook.ipynb`  
  Notebook com EDA, imputações, justificativas e avaliação das distribuições (antes vs depois).
- `Penguins_Dashboard_BI.pbix`  
  Dashboard no Power BI (base original + base imputada). 
- `Penguins_Dashboard_BI_pdf.pdf`  
  Exportação do dashboard para PDF (visão rápida). 
- `Penguins Dataset - Relatório Final.pdf`  
  Relatório com metodologia, justificativas e conclusões. 

---

## ✅ O que foi implementado (mapeado ao enunciado)

### 1) Dashboard com os dados da base inicial (ANTES)
Foram criados dashboards em Power BI a partir da base com valores ausentes, evidenciando categorias como “em branco” e “ilha desconhecida”, e o impacto dos NaNs nas análises por espécie/ilha/sexo. 

**Principais visuais (antes):**
- Massa corporal média e tamanho médio da asa (antes)
- Comprimento médio do bico e profundidade média do bico (antes) 

---

### 2) Imputação de colunas numéricas + justificativas
**Colunas numéricas tratadas:** `bill_length_mm`, `bill_depth_mm`, `flipper_length_mm`, `body_mass_g`. 

**Técnica escolhida:** **KNN Imputer (K=5, weights='distance')**, por utilizar registros semelhantes (“vizinhos”) ao invés de um valor global (como média/mediana), reduzindo distorções e respeitando o contexto local dos dados. 

**Pré-processamento:** normalização com **MinMaxScaler** (0 a 1), necessária porque o KNN usa distância e as variáveis estão em escalas diferentes (gramas vs milímetros). Depois, foi feita a desnormalização para retornar às unidades originais. 

**Avaliação:** comparação visual das distribuições antes/depois indicou preservação do formato geral e melhora na consistência, com curvas mais simétricas e menos “picos” artificiais. 

---

### 3) Imputação de colunas categóricas + justificativas
**Colunas categóricas tratadas:** `species`, `island`, `sex`. 

**Para `species` e `island`:** método **Forward Fill (ffill)**, escolhido porque havia organização sequencial em blocos (linhas seguidas com mesma espécie/ilha). Isso evita imputações aleatórias e mantém coerência local. 

**Para `sex`:** imputação por **característica morfológica**, relacionando `sex` com `bill_depth_mm` **dentro de cada espécie**, usando **medianas** (mais robustas a outliers) e atribuindo o sexo cuja mediana estivesse mais próxima do valor do registro. 

---

### 4) Dashboard com os dados imputados (DEPOIS)
Após a imputação, os dashboards passaram a exibir análises mais completas, sem categorias “em branco/desconhecido”, permitindo comparações mais confiáveis entre espécie/ilha/sexo. 

No dashboard imputado, por exemplo, destacam-se padrões como:
- Gentoo machos de Biscoe com maior massa corporal média. 
- Biscoe com maiores médias de nadadeira em vários grupos. 

---

## 🛠 Tecnologias utilizadas
- **Python (Jupyter Notebook)**: pandas, numpy, scikit-learn (KNNImputer, MinMaxScaler) 
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


