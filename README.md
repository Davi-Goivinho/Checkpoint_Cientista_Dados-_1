# ☕ Análise de Impacto do Consumo de Café na Qualidade do Sono

## 📋 Sobre o Projeto
Este projeto foi desenvolvido como parte do *Checkpoint de Cientista de Dados (Nível 1) da Alura

O objetivo central é analisar como o consumo diário de café influencia a qualidade e duração do sono dos indivíduos, cruzando dados de estilo de vida, demografia e saúde, além de construir modelo de Machine Learning capaz de prever a qualidade do sono e gerar recomendações.


## Estrutura do Repositório

```text
├── data/
│   ├── synthetic_coffee_health_10000.csv    # Dataset bruto com 10.000 registros
│   └── processed_coffee_health.csv          # Dataset processado
├── models/                                  # Modelos preditivos treinados salvos
├── notebooks/                               # Notebooks Jupyter com as análises
│   └── analise_cafe_sono.ipynb              # Notebook
├── reports/                                 # Documentação aprofundada e relatórios das entregas
│   └── parte_1_eda.md                       # Relatório completo da Entrega #1 (EDA)
├── .gitignore                              
├── pyproject.toml                           
├── uv.lock                                  
└── README.md                                # Documentação e apresentação do projeto
```



## Entregas do Projeto

- [x] **Entrega #1: Análise Exploratória de Dados (EDA)** — Documentação em [`reports/parte_1_eda.md`](reports/parte_1_eda.md) e código em [`notebooks/analise_cafe_sono.ipynb`](notebooks/analise_cafe_sono.ipynb)
- [ ] **Entrega #2: Visualização e Insights de Negócio**
- [ ] **Entrega #3: Modelo Preditivo & Recomendações**

---

## Ambiente e Reprodução com UV

Este projeto utiliza o gerenciador de pacotes e ambientes uv

### Pré-requisitos
- Linux (Ubuntu) ou qualquer sistema compatível com Python >= 3.10
- uv instalado

### Passos para reprodução

1. Clone o repositório:
```bash
git clone <url-do-repositorio>
cd Checkpoint_cientista_dados_Nivel_1
```

2. Instale as dependências sincronizadas pelo uv.lock:
```bash
uv sync
```

3. Inicie o Jupyter Lab:
```bash
uv run jupyter lab
```
