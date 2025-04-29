# 📊 Página - Painel de Entregas

## 🔧 Objetivo
Esta página foi desenvolvida para monitorar o desempenho das entregas, focando na análise da eficiência das transportadoras. 
Ela contém cartões indicadores de desempenho, métricas de entregas no prazo, fora do prazo, peso das entregas e um 
comparativo com o ano anterior. Além disso, inclui uma matriz para comparar ano, faturamento, frete e margem de lucro. 
Por fim, dois gráficos de barras apresentam o desempenho das cidades em termos de entregas no prazo e fora do prazo.

![Visualização Página - Painel de entregas](./Imagem/pag2.png)

# 📐 Medidas DAX – Página Painel de Entregas.
---

### 🎯 Medidas Criadas

```dax
Total de NFs Emitidas = SUM(Fato_Entregas[quantidade_nfs])
```
> Descrição: Soma o total de NFs (Notas Fiscais) emitidas, representando o total de documentos gerados para as entregas realizadas.
---

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

---

```dax
Peso Total = SUM(Fato_Entregas[peso_total])

```
> Descrição: Soma o peso total de todas as entregas realizadas. Esse valor é útil para entender a carga movimentada durante o período.
---

```dax
Eficiência Geral = DIVIDE([Total de Entregas no Prazo], [Total de Entregas])

```
> Descrição: Calcula a eficiência geral de entrega, com base no número de entregas realizadas no prazo em relação ao total de entregas.
---

```dax
Variação LY Total NFs Emitidas = 
VAR LY = CALCULATE([Total de NFs Emitidas], SAMEPERIODLASTYEAR(Dim_Tempo[Data]))
RETURN DIVIDE([Total de NFs Emitidas] - LY, LY)
```
> Descrição: Calcula a variação percentual das NFs emitidas em relação ao ano anterior.
---
```dax
Variação LY Entregas no Prazo = 
VAR LY = CALCULATE([Total de Entregas no Prazo], SAMEPERIODLASTYEAR(Dim_Tempo[Data]))
RETURN DIVIDE([Total de Entregas no Prazo] - LY, LY)
```
> Descrição: Calcula a variação percentual das entregas no prazo em relação ao ano anterior.
---


```dax
Variação LY Entregas Fora do Prazo = 
VAR LY = CALCULATE([Total de Entregas Fora do Prazo], SAMEPERIODLASTYEAR(Dim_Tempo[Data]))
RETURN DIVIDE([Total de Entregas Fora do Prazo] - LY, LY)

```
> Descrição: Calcula a variação percentual das entregas fora do prazo em relação ao ano anterior.
---

```dax
Variação LY Peso Total = 
VAR LY = CALCULATE([Peso Total], SAMEPERIODLASTYEAR(Dim_Tempo[Data]))
RETURN DIVIDE([Peso Total] - LY, LY)

```
> Descrição: Calcula a variação percentual do peso total das entregas em relação ao ano anterior.
---

```dax
Variação LY Eficiência Geral = 
VAR LY = CALCULATE([Eficiência Geral], SAMEPERIODLASTYEAR(Dim_Tempo[Data]))
RETURN DIVIDE([Eficiência Geral] - LY, LY)
```
> Descrição: Calcula a variação percentual da eficiência geral das entregas (entregas no prazo) em relação ao ano anterior.
---

```dax
% Entregas Fora do Prazo = DIVIDE([Total de Entregas Fora do Prazo], [Total de Entregas])

```
> Descrição: Calcula o percentual de entregas realizadas fora do prazo em relação ao total de entregas realizadas.
---

```dax
% Entregas no Prazo = DIVIDE([Total de Entregas no Prazo], [Total de Entregas])

```
> Descrição: Calcula o percentual de entregas realizadas dentro do prazo em relação ao total de entregas realizadas.
---


```dax
Comparativo LY Faturamento = 
VAR LY = CALCULATE([Faturamento], SAMEPERIODLASTYEAR(Dim_Tempo[Data]))
RETURN DIVIDE([Faturamento] - LY, LY)

```
> Descrição: Compara o faturamento do período atual com o faturamento do mesmo período do ano anterior.
---

```dax
Comparativo LY Frete = 
VAR LY = CALCULATE([Frete Total], SAMEPERIODLASTYEAR(Dim_Tempo[Data]))
RETURN DIVIDE([Frete Total] - LY, LY)

```
>  Descrição: Compara o valor do frete do período atual com o valor do frete do mesmo período do ano anterior.
---

```dax
Comparativo LY Margem de Lucro = 
VAR LY = CALCULATE([Margem de Lucro %], SAMEPERIODLASTYEAR(Dim_Tempo[Data]))
RETURN DIVIDE([Margem de Lucro %] - LY, LY)

```
> Descrição: Compara a margem de lucro percentual do período atual com a margem de lucro percentual do mesmo período do ano anterior.
---
