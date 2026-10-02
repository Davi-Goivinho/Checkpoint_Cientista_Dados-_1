# ☕ Análise de Impacto do Consumo de Café na Qualidade do Sono

## 📋 Sobre o Projeto
Este projeto foi desenvolvido como parte do **Checkpoint de Cientista de Dados (Nível 1)** da Alura, em parceria com a empresa de inteligência em saúde **Health&Life Analytics**.

O objetivo central é analisar minuciosamente como o consumo diário de café e a ingestão de cafeína influenciam a qualidade e a duração do sono dos clientes, cruzando variáveis de estilo de vida, saúde e demografia, além de construir modelos de Machine Learning capazes de prever a qualidade do sono e gerar recomendações preventivas para o negócio.

---

## 🏗️ Estrutura do Repositório

```text
├── data/
│   ├── synthetic_coffee_health_10000.csv    # Dataset bruto original com 10.000 registros
│   └── processed_coffee_health.csv          # Dataset tratado com feature engineering
├── models/
│   └── best_sleep_quality_model.joblib      # Pipeline completo do melhor modelo (Random Forest)
├── notebooks/
│   └── analise_cafe_sono.ipynb              # Notebook Jupyter com código limpo e comentários técnicos
├── reports/                                 # Relatórios analíticos e documentação em Markdown
│   ├── parte_1_eda.md                       # Documentação da Entrega #1 (Análise Exploratória de Dados)
│   ├── parte_2_insights.md                  # Documentação da Entrega #2 (Visualização e Insights de Negócio)
│   └── parte_3_modelagem.md                 # Documentação da Entrega #3 (Modelagem Preditiva e Recomendações)
├── .gitignore                               # Arquivos e diretórios ignorados pelo Git
├── pyproject.toml                           # Configuração do projeto e dependências (UV)
├── uv.lock                                  # Lockfile de dependências determinísticas
└── README.md                                # Documentação e apresentação principal do projeto
```

---

## 📌 Entregas do Projeto

- [x] **Entrega #1: Análise Exploratória de Dados (EDA)**
  - Relatório detalhado: [`reports/parte_1_eda.md`](reports/parte_1_eda.md)
  - Código: [`notebooks/analise_cafe_sono.ipynb`](notebooks/analise_cafe_sono.ipynb)
- [x] **Entrega #2: Visualização e Insights de Negócio**
  - Relatório detalhado: [`reports/parte_2_insights.md`](reports/parte_2_insights.md)
  - Código: [`notebooks/analise_cafe_sono.ipynb`](notebooks/analise_cafe_sono.ipynb)
- [x] **Entrega #3: Modelo Preditivo & Recomendações**
  - Relatório detalhado: [`reports/parte_3_modelagem.md`](reports/parte_3_modelagem.md)
  - Código: [`notebooks/analise_cafe_sono.ipynb`](notebooks/analise_cafe_sono.ipynb)
  - Artefato do modelo: [`models/best_sleep_quality_model.joblib`](models/best_sleep_quality_model.joblib)
  - Base processada: [`data/processed_coffee_health.csv`](data/processed_coffee_health.csv)

---

## 🌟 Principais Descobertas e Resultados

1. **Déficit de Sono em Altos Consumidores de Café:**
   Clientes no decil de maior consumo ($\ge 4,4$ xícaras/dia) dormem em média **47 minutos a menos por noite** em comparação àqueles com consumo residual ($\le 0,5$ xícara/dia).
2. **Impacto Severo do Estresse:**
   O estresse alto reduz a duração do sono em **2,80 horas por noite (-38,6%)** em relação ao estresse baixo e concentra 100% dos casos de qualidade classificados como **Poor**.
3. **Desempenho dos Modelos Preditivos:**
   - **Regressão Logística:** Acurácia Treino 99,36% | Teste 99,00% | F1-Score Macro 0,985
   - **Random Forest (Melhor Modelo):** Acurácia Treino 99,99% | Teste 99,10% | F1-Score Macro 0,990
   - **Diagnóstico:** Generalização excelente sem sinais de overfitting prejudicial (delta $< 0,9\%$).

---

## ⚙️ Ambiente e Reprodução com UV

Este projeto utiliza o gerenciador de pacotes e ambientes ultrarrápido **[uv](https://docs.astral.sh/uv/)**.

### Pré-requisitos
- Sistema operacional: Linux (Ubuntu) ou qualquer ambiente compatível com Python >= 3.10
- Gerenciador **uv** instalado ([Guia Oficial](https://docs.astral.sh/uv/getting-started/installation/))

### Como executar

1. Clone o repositório:
```bash
git clone <url-do-seu-repositorio>
cd Checkpoint_cientista_dados_Nivel_1
```

2. Sincronize o ambiente virtual e dependências:
```bash
uv sync
```

3. Abra o Jupyter Lab ou Jupyter Notebook:
```bash
uv run jupyter lab
# ou
uv run jupyter notebook
```

---

## ✅ Autoavaliação de Pontos de Revisão (Alura)

| Ponto de Revisão | Status | Onde Encontrar |
|---|---|---|
| Repositório Git acessível e organizado | ✅ Atendido | Raiz do repositório |
| README.md explicativo com objetivo e reprodução | ✅ Atendido | [`README.md`](README.md) |
| Executável em Jupyter / Google Colab sem erros | ✅ Atendido | [`notebooks/analise_cafe_sono.ipynb`](notebooks/analise_cafe_sono.ipynb) |
| Dataset disponível ou indicado | ✅ Atendido | [`data/synthetic_coffee_health_10000.csv`](data/synthetic_coffee_health_10000.csv) |
| **Entrega #1:** EDA com distribuições numéricas e categóricas | ✅ Atendido | [`reports/parte_1_eda.md`](reports/parte_1_eda.md) |
| **Entrega #2:** Gráficos comparativos e Principais Descobertas | ✅ Atendido | [`reports/parte_2_insights.md`](reports/parte_2_insights.md) |
| **Entrega #3:** Pré-processamento, encoding e feature derivada | ✅ Atendido | [`notebooks/analise_cafe_sono.ipynb`](notebooks/analise_cafe_sono.ipynb) |
| **Entrega #3:** Pelo menos 2 modelos comparados com métricas | ✅ Atendido | [`reports/parte_3_modelagem.md`](reports/parte_3_modelagem.md) |
| **Entrega #3:** Dataset processado em CSV salvo | ✅ Atendido | [`data/processed_coffee_health.csv`](data/processed_coffee_health.csv) |
| **Entrega #3:** Melhor modelo salvo | ✅ Atendido | [`models/best_sleep_quality_model.joblib`](models/best_sleep_quality_model.joblib) |
| **Entrega #3:** Recomendações para o Negócio | ✅ Atendido | [`reports/parte_3_modelagem.md`](reports/parte_3_modelagem.md) |
