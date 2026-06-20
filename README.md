# The Impact of Model Selection Metrics during Hyperparameter Tuning on Algorithmic Fairness
### An Empirical Study | Um Estudo Empírico

> 🇧🇷 *O Impacto das Métricas de Seleção de Modelos durante o Ajuste de Hiperparâmetros na Equidade Algorítmica*

**Published at / Publicado no:** SEMISH 2026 – Seminário Integrado de Software e Hardware  
**Authors / Autores:** Bianca Matos de Barros, Diego Dimer Rodrigues, Gabriela Bellardinelli Oliveira, Mariana Recamonde-Mendoza  
**Institution / Instituição:** Instituto de Informática – UFRGS & Núcleo de Bioinformática – HCPA

---

## Abstract / Resumo

🇺🇸 **[EN]** The growing use of machine learning in high-stakes domains raises concerns about fairness. This study systematically investigates how seven performance metrics used during **hyperparameter tuning and model selection** affect fairness outcomes across five benchmark datasets. Results show that metrics are not neutral: recall-based optimization yields higher disparities, while precision and specificity lead to more balanced outcomes, with PR-AUC showing intermediate behavior. Overall, metric choice influences fairness, but outcomes are largely driven by dataset characteristics, with optimization redistributing errors rather than eliminating bias.

🇧🇷 **[PT-BR]** O uso crescente de aprendizado de máquina em domínios críticos levanta preocupações sobre equidade algorítmica. Este estudo investiga sistematicamente como sete métricas de desempenho usadas durante o **ajuste de hiperparâmetros e seleção de modelos** afetam os resultados de justiça em cinco conjuntos de dados de benchmark. Os resultados mostram que as métricas não são neutras: a otimização baseada em *recall* produz maiores disparidades, enquanto precisão e especificidade levam a resultados mais equilibrados, com PR-AUC apresentando comportamento intermediário.


## Repository Structure / Estrutura do Repositório

```
semish2026_OptimizationMetrics-Bias/
│
├── datasets/                          # Benchmark datasets (preprocessed)
│   ├── adult_converted.csv
│   ├── compas-scores-raw_converted.csv
│   ├── dropout_converted.csv
│   ├── heart_converted.csv
│   └── intersectional-bias_converted.csv
│
├── results/                           # Output 
├── ├── raw_results.csv                    # Raw predictions (~840k rows)
├── main.ipynb                         # Experimental pipeline
├── requirements.txt                   # Python dependencies
└── README.md
```

---

## Methodology / Metodologia

🇺🇸 **[EN]** The pipeline evaluates **2 tree-based models** (Random Forest and Gradient Boosting) tuned with **7 optimization metrics** under a **Nested Stratified Cross-Validation** scheme (3-fold outer × 3-fold inner), with stratification on both the target variable and the protected attribute. Post-training fairness is measured using three complementary metrics.

🇧🇷 **[PT-BR]** O pipeline avalia **2 modelos baseados em árvore** (Random Forest e Gradient Boosting) ajustados com **7 métricas de otimização** sob um esquema de **Validação Cruzada Aninhada e Estratificada** (3-fold externo × 3-fold interno), com estratificação tanto na variável alvo quanto no atributo protegido.

### Optimization Metrics / Métricas de Otimização
`Accuracy` · `Precision` · `Recall` · `Specificity` · `ROC-AUC` · `PR-AUC` · `MCC`

### Fairness Metrics / Métricas de Equidade
| Metric | Description |
|---|---|
| **Disparate Impact (DI)** | Ratio of favorable predictions between unprivileged and privileged groups. DI ∈ [0.8, 1.25] is the fairness threshold. |
| **Sensitivity Gap** | Absolute difference in True Positive Rate (TPR) between groups. |
| **Average Absolute Odds Difference (AAOD)** | Average of absolute differences in FPR and TPR across groups. AAOD = 0 means perfect equality of odds. |

---

## Key Findings / Principais Resultados

- **Metrics are not neutral** — optimization objectives shape error distributions across sociodemographic subgroups in measurable ways.
- **Recall** is consistently associated with the highest disparity levels across all fairness metrics.
- **Precision and Specificity** tend to produce the most balanced error distributions.
- **PR-AUC** offers an intermediate trade-off, avoiding extreme disparities without consistently achieving the lowest unfairness.
- **Dataset characteristics dominate** — the direction and magnitude of bias are primarily driven by the data, not by the optimization metric.
- **No standard metric resolves the performance–fairness trade-off** — optimization redistributes errors along a constrained Pareto frontier rather than eliminating it.

---

## Installation / Instalação

```bash
git clone https://github.com/mlab-inf-ufrgs/semish2026_OptimizationMetrics-Bias.git
cd semish2026_OptimizationMetrics-Bias
pip install -r requirements.txt
```

> 🇺🇸 We strongly recommend running this pipeline in an isolated virtual environment (`venv` or `conda`) to avoid dependency conflicts.  
> 🇧🇷 Recomendamos fortemente a execução em um ambiente virtual isolado (`venv` ou `conda`) para evitar conflitos de dependências.


## Contact / Contato

`{bmbarros, ddrodrigues, gboliveira, mrmendoza}@inf.ufrgs.br`  
Instituto de Informática – Universidade Federal do Rio Grande do Sul (UFRGS)
