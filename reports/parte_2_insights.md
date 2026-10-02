# 💡 Entrega #2: Visualização e Insights de Negócio


## 1. Visão Geral da Análise Comparativa
Nesta segunda parte, aprofundamos nas relações dos hábitos de consumo de café, fatores de estresse, estilo de vida, características e duração do sono dos 10k clientes da base.



## 2. Relação Comparativa: Consumo de Café e Horas de Sono

A dispersão com reta de regressão linear e os boxplots confirmam uma tendência de redução de sono à medida que o consumo de café aumenta

| Categoria de Qualidade do Sono | Media de Xícaras de Café / dia | Ingestão Média de Cafeína (mg) | Média de Horas de Sono / noite |
|---|---|---|---|
| **Excellent** | 2,05 xíc | 194,7 mg | 8,59 h |
| **Good** | 2,45 xíc | 232,5 mg | 6,92 h |
| **Fair** | 2,76 xíc | 262,7 mg | 5,58 h |
| **Poor** | 2,98 xíc | 283,2 mg | 4,45 h |

> Observação Há uma relação decrescente: a cada degrau de piora na qualidade do sono, observa-se um aumento no consumo de café e uma queda nas horas dormidas.

## 3. Análises Segmentadas por Grupos

### 3.1 Segmentação por Gênero
- **Feminino, Masculino e Outro:** Média de sono de 6,64 horas (mediana 6,60h).
- *Conclusão:* Não há diferença significativa no padrão de sono entre os gêneros

### 3.2 Segmentação por Faixa Etária
- **18 a 30 anos:** Média de 6,64 horas de sono | Consumo médio: 2,53 xícaras de café.
- **31 a 45 anos:** Média de 6,64 horas de sono | Consumo médio: 2,51 xícaras de café.
- **46 a 60 anos:** Média de 6,63 horas de sono | Consumo médio: 2,47 xícaras de café.
- **Acima de 60 anos:** Média de 6,62 horas de sono | Consumo médio: 2,45 xícaras de café.
- *Conclusão:* A duração do sono e a ingestão de café permanecem estáveis ao longo de todas as faixas.

### 3.3 Segmentação por Ocupação Profissional
- **Healthcare (Profissionais de Saúde):** 6,67 h de sono.
- **Student (Estudantes):** 6,64 h de sono.
- **Service (Setor de Serviços):** 6,63 h de sono.
- **Other (Outras Ocupações):** 6,62 h de sono.
- **Office (Escritório / Corporativo):** 6,61 h de sono.
- *Conclusão:* Sem grande diferença na duração média do sono entre as ocupações.


## 4. O Impacto Combinado de Café e Estresse

A interação entre nível de estresse e faixas de ingestão de cafeína

| Nível de Estresse | Baixo Cafeína ($\le 150$ mg) | Moderado Cafeína ($151-300$ mg) | Alto Cafeína ($> 300$ mg) | Média Global por Estresse |
|---|---|---|---|---|
| **Low (Baixo)** | 7,39 h | 7,23 h | 7,11 h | **7,25 h** |
| **Medium (Médio)** | 5,59 h | 5,59 h | 5,56 h | **5,58 h** |
| **High (Alto)** | 4,43 h | 4,46 h | 4,45 h | **4,45 h** |

### Interpretação do Efeito de Interação:
1. O estresse é o fator estrutural dominante: Clientes sob estresse alto dormem em média apenas 4,45h por noite, independentemente da faixa de café.
2. O café atua como modulador fino no grupo de baixo estressePa    indivíduos com baixo nível de estresse, quem consome alto teor de cafeína dorme cerca de 17 minutos diários a menos do que quem tem baixo consumo.


## Principais Descobertas (Destaques Quantitativos de Negócio)

1. **Impacto nos Extremos de Consumo de Café:**
   > *"Clientes de maior consumo de café (maior ou igual a 4,4 xícaras/dia) dormem em média 47 minutos a menos por noite.*
2. **Impacto do Estresse na Duração e Qualidade do Sono:**
   > *"O nível de estresse alto acarreta uma redução drástica de 2,80 horas de sono por noite em relação ao estresse baixo, além de concentrar 100% dos casos de qualidade de sono classificados como Poor."*
3. **Associação Monotônica entre Cafeína e Qualidade do Sono:**
   > *"A ingestão diária média de cafeína entre indivíduos com qualidade de sono Poor é 45,5% superior à dos indivíduos com qualidade Excellent."*
4. **Universalidade do Efeito:**
   > *"Os efeitos de perda de horas de sono correlacionados ao café e ao estresse são homogêneos entre homens e mulheres e a todas as faixas etárias e ocupações analisadas."*


## Implicações para a Health&Life Analytics

- O manejo do estresse deve ser o pilar primário de qualquer de saúde, pois o estresse severo anula grande parte dos benefícios de bons hábitos isolados.
- Na Parte 3, utilizaremos essas interações para treinar algoritmos de Machine Learning capazes de prever a classe exata de qualidade do sono Sleep_Quality.
