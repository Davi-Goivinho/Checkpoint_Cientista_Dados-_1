# 📊 Análise Exploratória de Dados (EDA)

 
**Arquivo de Código:** [`notebooks/analise_cafe_sono.ipynb`](../notebooks/analise_cafe_sono.ipynb)  
**Base de Dados:** `data/synthetic_coffee_health_10000.csv`

## 1. Visão Geral da Base de Dados

A base de dados reúne registros de 10.000 pessoas de 20 países, com 16 variáveis que demonstram hábitos de consumo do café como ingestão de cafeína diária, padrões de sono, indicadores antropométrico, nível de estresse e estilo de vida.

### 1.1 Auditoria Estrutural e Qualidade dos Dados
- **Dimensões:** 10.000 linhas × 16 colunas.
- **Registros Duplicados:** 0 linhas duplicadas detectadas.
- **Tratamento de Valores Ausentes:**
  - O dataset não possui valores ausentes no sentido padrão (NAN), porém, a coluna `Health_Issues` apresenta o valor "NONE" em 5.941 registros, indicando ausência de problemas de saúde. Para evitar interpretações erradas, mantive esses dados na base.


## 2. Estatísticas Descritivas das Variáveis Numéricas

| Variáveis | Média | Desvio Padrão | Mediana | Mínimo | Máximo | Intervalo Interquartil (IQR) |
|---|---|---|---|---|---|---|
| **Consumo de Café (Coffee_Intake)** | 2,51 xíc | 1,46 | 2,40 xí | 0,00 | 8,20 xíc | 2,00 |
| **Ingestão de Cafeína (Caffeine_mg)** | 238,41 mg | 138,59 | 228,05 mg | 0,00 | 780,30 mg | 189,98 |
| **Horas de Sono (Sleep_Hours** | 6,64 h | 1,28 | 6,60 h | 3,00 | 10,00 h | 1,70 |
| **Idade (Age)** | 34,95 anos | 11,88 | 33,00 anos | 18,00 | 80,00 anos | 16,00 |
| **Índice de Massa Corporal (BMI)** | 23,99 | 3,92 | 23,90 | 15,00 | 38,20 | 5,30 |
| **Frequência Cardíaca (Heart_Rate)** | 70,62 bpm | 9,84 | 70,00 bpm | 50,00 | 109,00 bpm | 13,00 |
| **Atividade Física (Physical_Activity_Hours)** | 7,49 h/sem | 4,25 | 7,40 h/sem | 0,00 | 15,00 h/sem | 7,40 |

## 3. Distribuição das Variáveis Categóricas

1. **Qualidade do Sono (Sleep_Quality):**
   - **Good:** 5637 clientes (56,4%)
   - **Fair:** 2050 clientes (20,5%)
   - **Excellent:** 1352 clientes (13,5%)
   - **Poor:** 961 clientes (9,6%)
2. **Nível de Estresse (Stress_Level):**
   - **Low:** 6989 clientes (69,9%)
   - **Medium:** 2050 clientes (20,5%)
   - **High:** 961 clientes (9,6%)
3. **Genero (Gender):**
   - **Feminino:** 5001 (50,0%)
   - **Masculino:** 4773 (47,7%)
   - **Outro:** 226 (2,3%)
4. **Condições de Saúde (Health_Issues):**
   - **None:** 5941 (59,4%)
   - **Mild:** 3579 (35,8%)
   - **Moderate:** 463 (4,6%)
   - **Severe:** 17 (0,2%)
5. **Hábitos de Risco:**
   - **Tabagismo:** 2004 fumantes (20,0%)
   - **Consumo de Álcool:** 3007 consumidres (30,1%)


## 4. Correlações e Primeiros Padrões Identificados

### 4.1 Correlação com Duração do Sono (Sleep_Hours)
- **Caffeine_mg:** -0,190
- **Coffee_Intake:** -0,190
- **Heart_Rate:** -0,036
- **Age, BMI, Atividade Física:** correlações próximas de 0

### 4.2 Consumo de Café vs. Qualidade do Sono
| Qualidade do Sono | Media Horas de Sono | Média Consumo Café (xícaras por dia) | Ingestão Média de Cafeína (mg por dia) |
|---|---|---|---|
| **Excelent** | 8,59 h | 2,05 | 194,7 mg |
| **Good** | 6,92 h | 2,45 | 232,5 mg |
| **Fair** | 5,58 h | 2,76 | 262,7 mg |
| **Poor** | 4,45 h | 2,98 | 283,2 mg |

> **Achado:** Clientes com sono Poor dormem em média 4,15 horas a menos e consomem 1 xícara a mais de café por dia em comparação com os clientes de sono Excellent.

### 4.3 Estresse vs. Qualidade do Sono
- **Estresse Alto:** 100% dos indivíduos relatam sono Poor.
- **Estresse Médio:** 100% dos indivíduos relatam sono Fair.
- **Estresse Baixo:** 81% relatam sono Good e 19% relatam sono Excellent.
- O estresse atua como um fator fundamental, estabelecendo faixas de qualidade que serão aprofundadas com cruzamentos e segmentações na parte 2.
