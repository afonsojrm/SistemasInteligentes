# Sistemas Inteligentes - 1ª Lista de Projetos

Implementação dos 5 problemas práticos de Machine Learning da disciplina de Sistemas Inteligentes (UFERSA - Semestre 2026.2).

Cada diretório foi estruturado com o respectivo **Jupyter Notebook (`.ipynb`)** com execução passo a passo em células individuais, base de dados, figuras salvas e relatório técnico com as justificativas.

---

## Estrutura do Repositório

```text
.
├── requirements.txt                   <- Dependências do projeto
│
├── problema_1_regressao_linear/       <- Previsão de energia (MW) na usina CCPP (Regressão Linear Múltipla)
│   ├── dataset/ccpp.csv
│   ├── graficos/                      <- Correlação, real vs previsto e resíduos
│   ├── problema_1.ipynb               <- Execução interativa passo a passo
│   └── relatorio.md                   <- Análise teórica e equações
│
├── problema_2_regressao_logistica/    <- Diagnóstico de cardiopatia (Regressão Logística)
│   ├── dataset/heart_cleveland.csv
│   ├── graficos/                      <- Curva ROC individual e matriz de confusão
│   ├── problema_2.ipynb
│   └── relatorio.md
│
├── problema_3_knn/                    <- Classificação de qualidade de vinhos (k-NN)
│   ├── dataset/winequality-red.csv
│   ├── graficos/                      <- Curva acurácia vs k e matriz de confusão
│   ├── problema_3.ipynb
│   └── relatorio.md
│
├── problema_4_arvore_decisao/         <- Avaliação de risco de crédito (Árvore de Decisão)
│   ├── dataset/german_credit.csv
│   ├── graficos/                      <- Curva de complexidade, árvore e matriz de confusão
│   ├── problema_4.ipynb
│   └── relatorio.md
│
└── problema_5_kmeans/                 <- Segmentação de clientes atacadistas (k-Means)
    ├── dataset/Wholesale_customers_data.csv
    ├── graficos/                      <- Boxplots de gastos, cotovelo, silhueta, perfis e PCA
    ├── problema_5.ipynb
    └── relatorio.md
```

---

## Como Executar

### 1. Instalação das Dependências

No terminal, instale os pacotes necessários:

```bash
pip install -r requirements.txt
```

### 2. Execução dos Notebooks

Os notebooks podem ser abertos e executados diretamente pelo **VS Code** ou pelo **Jupyter Lab / Notebook**:

1. No VS Code, abra o arquivo `.ipynb` do problema desejado na barra lateral esquerda.
2. Selecione o kernel do Python no canto superior direito (`Select Kernel` -> selecione o ambiente Python 3.12).
3. Execute célula a célula com `Shift + Enter` ou clique em **Run All** no topo para rodar todas as células em sequência.

> **Nota:** Todos os notebooks já foram pré-executados e salvos com as tabelas e gráficos renderizados. Ao visualizá-los diretamente no GitHub ou no VS Code, todos os resultados já aparecem imediatamente.

---

## Resumo dos Modelos e Resultados

| Problema | Modelo | Variável Alvo | Principais Variáveis e Unidades | Métrica Principal | Destaque Técnico |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1. CCPP** | Regressão Linear Múltipla | `PE` (Potência Líquida, MW) | `AT` (°C), `V` (cm Hg), `AP` (mbar), `RH` (%) | $R^2 = 0.9301$<br>$\text{RMSE} = 4.50\text{ MW}$ | Forte influência negativa da temperatura ambiente ($r = -0.95$) na geração de energia. |
| **2. Cardiopatia** | Regressão Logística (`liblinear`) | `target` (0: Saudável, 1: Cardiopatia) | `ca` (vasos), `thal`, `thalach` (bpm), `oldpeak` (mm) | $\text{Recall} = 92.86\%$<br>$\text{AUC} = 0.9513$ | Prioridade ao recall clínico para evitar falsos negativos em pacientes graves. |
| **3. Vinhos** | $k$-NN ($k=11$) | `qualidade` (ruim, médio, bom) | 11 atributos químicos (álcool, sulfatos, acidez) | $\text{Acurácia} = 77.81\%$ | Normalização obrigatória por distância Euclidiana; maior confusão entre classes adjacentes (ruim e médio). |
| **4. Crédito** | Árvore de Decisão | `Risk` (0: Bom, 1: Mau) | `duration` (meses), `credit_amount` (DM), saldo | $\text{Profundidade} = 5$<br>$\text{F1} = 0.81$ | Regras auditáveis; balanceamento de classes reduz falsos positivos em empréstimos de alto risco. |
| **5. Clientes** | $k$-Means ($k=2$) | Segmentação (sem rótulos) | Gastos anuais em `Fresh`, `Milk`, `Grocery`, etc. | $\text{Silhueta} = 0.2903$<br>$\text{ARI} = 0.5135$ | Reconstrução do canal comercial (Horeca vs Varejo) sem usar rótulos no treinamento. |
