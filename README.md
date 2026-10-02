# ☕ Análise de Impacto do Consumo de Café na Qualidade do Sono

## 📋 Sobre o Projeto
Este projeto foi desenvolvido como parte do **Checkpoint de Cientista de Dados (Nível 1)** da Alura, em parceria com a empresa fictícia **Health&Life Analytics**.

O objetivo central é investigar minuciosamente como o consumo diário de café e a ingestão de cafeína influenciam a qualidade e duração do sono dos indivíduos, cruzando dados de estilo de vida, demografia e saúde, além de construir modelos de Machine Learning capazes de prever a qualidade do sono e gerar recomendações orientadas a negócio.

---

## 🏗️ Estrutura do Repositório

```text
├── data/
│   ├── synthetic_coffee_health_10000.csv    # Dataset bruto com 10.000 registros
│   └── processed_coffee_health.csv          # Dataset processado e com feature engineering
├── models/                                  # Modelos preditivos treinados salvos
├── notebooks/                               # Notebooks Jupyter com as análises
│   └── analise_cafe_sono.ipynb              # Notebook completo (EDA, Insights e Modelagem)
├── .gitignore                               # Arquivos e diretórios ignorados pelo Git
├── pyproject.toml                           # Especificação do projeto e dependências (UV)
├── uv.lock                                  # Lockfile de dependências determinísticas
└── README.md                                # Documentação e apresentação do projeto
```

---

## ⚙️ Ambiente e Reprodução com UV

Este projeto utiliza o gerenciador de pacotes e ambientes ultrarrápido **[uv](https://docs.astral.sh/uv/)**.

### Pré-requisitos
- Linux (Ubuntu) ou qualquer sistema compatível com Python >= 3.10
- `uv` instalado ([Guia de Instalação](https://docs.astral.sh/uv/getting-started/installation/))

### Passos para reprodução

1. Clone o repositório:
```bash
git clone <url-do-repositorio>
cd Checkpoint_cientista_dados_Nivel_1
```

2. Instale as dependências sincronizadas pelo `uv.lock`:
```bash
uv sync
```

3. Inicie o Jupyter Notebook ou Jupyter Lab:
```bash
uv run jupyter lab
# ou
uv run jupyter notebook
```
