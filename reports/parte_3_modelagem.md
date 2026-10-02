# 🤖 Entrega #3: Modelo Preditivo & Recomendações para o Negócio

**Empresa Parceira:** Health&Life Analytics  
**Arquivo de Código:** [`notebooks/analise_cafe_sono.ipynb`](../notebooks/analise_cafe_sono.ipynb)  
**Artefato do Modelo:** [`models/best_sleep_quality_model.joblib`](../models/best_sleep_quality_model.joblib)  
**Dataset Processado:** [`data/processed_coffee_health.csv`](../data/processed_coffee_health.csv)

---

## 1. Visão Geral da Modelagem

O objetivo central desta entrega é desenvolver e validar modelos de Machine Learning supervisionados para prever a qualidade do sono (`Sleep_Quality`) dos clientes a partir do seu perfil de hábitos (consumo de café, cafeína), estilo de vida, condições fisiológicas e indicadores sociodemográficos.

A variável alvo possui 4 classes ordinais:
- **Poor (Sono Ruim)**
- **Fair (Sono Regular)**
- **Good (Sono Bom)**
- **Excellent (Sono Excelente)**

---

## 2. Pré-processamento e Engenharia de Features

### 2.1 Limpeza e Seleção de Atributos
- **Remoção de Identificador:** A coluna `ID` foi descartada por não conter valor preditivo.
- **Tratamento Categórico:** A coluna `Health_Issues` manteve a integridade de sua categoria `"None"` (ausência de patologia).

### 2.2 Criação de Features Derivadas (Feature Engineering)
Foram construídas duas variáveis derivadas baseadas em hipóteses clínicas e comportamentais:
1. **`Caffeine_per_BMI` ($\text{mg/BMI}$):** Razão entre a cafeína ingerida e o Índice de Massa Corporal. Permite avaliar a dosagem do estimulante em relação ao porte antropométrico do indivíduo.
2. **`Sleep_to_Coffee_Ratio` ($\text{horas/xícara}$):** Razão entre a média de horas dormidas e as xícaras de café diárias (adicionado $+1.0$ para suavização e evitar divisão por zero). Mede a eficiência do descanso frente à carga diária de consumo.

### 2.3 Estrutura de Pipelines do Scikit-Learn
Para evitar qualquer risco de vazamento de dados (*data leakage*), o pré-processamento foi encapsulado em um `ColumnTransformer`:
- **Variáveis Numéricas Contínuas:** Padronizadas via `StandardScaler()`.
- **Variáveis Categóricas Nominais/Ordinais:** Codificadas via `OneHotEncoder(drop='first', handle_unknown='ignore')`.
- **Variáveis Binárias:** Mantidas em escala binária via `passthrough`.

### 2.4 Divisão dos Dados
- **Treino:** 8.000 amostras (80%)
- **Teste:** 2.000 amostras (20%)
- **Estratificação:** Divisão estratificada pela variável alvo `Sleep_Quality` para assegurar que a proporção de cada uma das 4 classes seja rigorosamente idêntica nos dois conjuntos.

---

## 3. Avaliação Comparativa dos Modelos

Foram implementados e comparados dois modelos de classificação supervisionada:
1. **Modelo 1:** Regressão Logística Multinomial (com regularização L2 e solver L-BFGS).
2. **Modelo 2:** Random Forest Classifier (com 100 estimadores e profundidade máxima `max_depth=12`).

### 3.1 Tabela Comparativa de Métricas

| Modelo | Acurácia (Treino) | Acurácia (Teste) | Delta (Overfitting) | F1-Score Macro (Teste) |
|---|---|---|---|---|
| **Regressão Logística** | 99,36% | 99,00% | **0,36%** | **0,985** |
| **Random Forest Classifier** | 99,99% | 99,10% | **0,89%** | **0,990** |

---

### 3.2 Relatório de Classificação Detalhado no Teste (Random Forest)

| Classe | Precisão (Precision) | Revocação (Recall) | F1-Score | Amostras no Teste (Support) |
|---|---|---|---|---|
| **Poor** | 1,00 | 1,00 | 1,00 | 192 |
| **Fair** | 1,00 | 1,00 | 1,00 | 410 |
| **Good** | 0,99 | 1,00 | 0,99 | 1.128 |
| **Excellent** | 0,99 | 0,94 | 0,97 | 270 |
| **Média Ponderada (Weighted Avg)** | **0,99** | **0,99** | **0,99** | **2.000** |

---

### 3.3 Matriz de Confusão no Teste (Random Forest)

```text
               Predito: Poor  Predito: Fair  Predito: Good  Predito: Excellent
Real: Poor           192            0              0                0
Real: Fair             0          410              0                0
Real: Good             0            0           1126                2
Real: Excellent        0            0             16              254
```

- **Classes Críticas (Poor e Fair):** Acurácia de 100% (zero falsos positivos e zero falsos negativos).
- **Classes Good vs. Excellent:** Apenas 18 amostras de 2.000 sofreram pequenas confusões na fronteira sutil entre sono Good e Excellent.

---

## 4. Diagnóstico dos Modelos: Overfitting vs. Underfitting

- **Modelo Escolhido:** O **Random Forest Classifier** apresentou o melhor desempenho geral, com **99,10% de acurácia no teste** e equilíbrio quase perfeito entre precisão e revocação em todas as 4 classes.
- **Avaliação de Overfitting:** Ambos os modelos exibiram uma diferença entre treino e teste extremamente baixa ($< 0,9\%$). Não há evidências de *overfitting* nocivo ou de *underfitting*, comprovando excelente capacidade de generalização em novos dados.
- **Importância dos Preditores (Feature Importance - Random Forest):**
  1. `Sleep_Hours` (43,5%): Horas de sono é o divisor primordial.
  2. `Stress_Level` (36,6%): O nível de estresse define a faixa de severidade.
  3. `Health_Issues` (7,5%): Condições de saúde prévias impactam a vulnerabilidade.
  4. `Sleep_to_Coffee_Ratio` (6,1%): A feature derivada criada capturou com sucesso o equilíbrio sono/café.
  5. `Caffeine_mg` e `Coffee_Intake` (2,2%): Estimulantes diretos que modulam a fronteira de qualidade.

---

## 5. Artefatos Exportados

1. **Dataset Processado:** Arquivo CSV contendo todas as variáveis tratadas e as novas features derivadas disponível em [`data/processed_coffee_health.csv`](../data/processed_coffee_health.csv).
2. **Modelo Salvo:** Pipeline completo com pré-processamento e Random Forest serializado via Joblib disponível em [`models/best_sleep_quality_model.joblib`](../models/best_sleep_quality_model.joblib).

---

## 🎯 6. Recomendações para o Negócio (Health&Life Analytics)

Com base nas evidências analíticas e no modelo preditivo validado, sugerimos as seguintes ações estratégicas para orientar os clientes:

### 1. Diretriz de Consumo Seguro de Cafeína
- **Limite Recomendado:** Orientar os clientes a não ultrapassar **200 mg a 250 mg de cafeína por dia** (aproximadamente 2 a 2,5 xícaras de café). Nossos dados demonstraram que clientes com consumo acima de 4 xícaras sofrem um déficit crônico de **47 minutos a menos de sono por noite**.
- **Corte Noturno:** Recomendar a interrupção da ingestão de cafeína pelo menos 6 a 8 horas antes do horário planejado para dormir, reduzindo o estímulo cardiovascular e simpático.

### 2. Protocolo Integrado de Gestão do Estresse
- O estresse provou ser a variável mais destrutiva para o sono: **100% dos clientes com estresse alto apresentaram sono classificado como Poor**.
- A empresa deve integrar programas de meditação guiada, respiração diafragmática e suporte psicológico em seu aplicativo, pois diminuir o estresse de Alto para Baixo pode recuperar até **2,8 horas de sono por noite**.

### 3. Sistema Preventivo no Aplicativo Baseado no Modelo Preditivo
- Integrar o modelo `best_sleep_quality_model.joblib` à plataforma móvel da Health&Life Analytics.
- Ao identificar um cliente que combina aumento súbito de xícaras de café com elevação de estresse, o sistema deve disparar **alertas preventivos personalizados** antes que o quadro evolua para privação crônica de sono e problemas cardiovasculares.
