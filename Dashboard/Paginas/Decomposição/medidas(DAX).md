# 📊 Página - Decomposição

## 🔧 Objetivo
O objetivo principal da página "Decomposição" é analisar de maneira detalhada o desempenho das entregas realizadas, 
segmentando os dados de forma granular por diferentes dimensões, como transportadora, cliente, e região. 
Através desta página, busco identificar insights importantes sobre as entregas no prazo e fora do prazo, 
proporcionando uma visão clara de como cada fator contribui para a eficiência logística. 
A decomposição dos dados ajuda a identificar áreas de melhoria e otimizar os processos operacionais, 
visando garantir a maximização da performance das transportadoras e a redução de entregas fora do prazo.

# 📐 Medidas DAX – Página Decomposição
---

### 🎯 Medidas Utilizadas

```dax
Entregas no Prazo = 
CALCULATE(
    COUNTROWS(Fato_Entregas),
    Fato_Entregas[data_entrega] <= Fato_Entregas[data_lead_time]
)
```
> Conta o número de entregas que foram realizadas no prazo (ou antes) do lead time previsto.
---
```dax
Total Entregas Fora do Prazo = CALCULATE(
    COUNTROWS(Fato_Entregas),
    Fato_Entregas[entregue_no_prazo] = "Não"
)
```
>  Total de entregas que não foram realizadas dentro do prazo estipulado.
---

