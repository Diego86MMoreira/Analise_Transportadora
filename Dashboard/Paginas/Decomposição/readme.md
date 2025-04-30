# 📊 Página - Decomposição

## 🔧 Objetivo
O objetivo principal da página "Decomposição" é analisar de maneira detalhada o desempenho das entregas realizadas, 
segmentando os dados de forma granular por diferentes dimensões, como transportadora, cliente, e região. 
Através desta página, busco identificar insights importantes sobre as entregas no prazo e fora do prazo, 
proporcionando uma visão clara de como cada fator contribui para a eficiência logística. 
A decomposição dos dados ajuda a identificar áreas de melhoria e otimizar os processos operacionais, 
visando garantir a maximização da performance das transportadoras e a redução de entregas fora do prazo.

![Visualização Página - Painel de entregas](../../../Imagem/pag3.png)

# 📐 Medidas DAX – Página Decomposição
---

### 🎯 Medidas Utilizadas

```dax
Total de Entregas no Prazo = CALCULATE(DISTINCTCOUNT(Fato_Entregas[id_entrega]), 
Fato_Entregas[entrega_prazo] = "Sim")
```
> Descrição: Conta o número de entregas realizadas dentro do prazo estipulado pela transportadora.

---

```dax
Total de Entregas Fora do Prazo = CALCULATE(DISTINCTCOUNT(Fato_Entregas[id_entrega]), 
Fato_Entregas[entrega_prazo] = "Não")

```
> Descrição: Conta o número de entregas realizadas fora do prazo estipulado.
