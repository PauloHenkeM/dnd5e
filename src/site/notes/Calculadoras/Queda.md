---
{"dg-publish":true,"permalink":"/calculadoras/queda/","title":"Calculadora de Queda","created":"2024-07-25T10:09:38.000-03:00"}
---


As seguintes calculadoras fornecerão informações sobre quedas, levando em consideração o arrasto. 
O limite de dano de queda do PHB é removido em favor da velocidade terminal (52,18 m/s). 
A escala de dano é calibrada de forma que 3 metros de queda correspondem exatamente a 1d6 de dano. 
As unidades disponíveis são m, ft, s e rodadas (6s).
___
- **Comprimento:** `INPUT[inlineSelect(option(0,m), option(1,ft)):dist_unit]`
- **Tempo:** `INPUT[inlineSelect(option(0,s), option(1,rounds)):time_unit]`

### Tempo
**Distância da queda:** `INPUT[number(class(nb-mb-css)):fall_dist]` `VIEW[{dist_unit} ? "ft" : "m"]`

**Velocidade da queda:** `VIEW[52.184894023 * tanh(acosh(exp((9.81*{fall_dist}*(1-0.6952*{dist_unit}))/52.184894023^2)))][math(hidden):v]` `VIEW[round((1+5*{time_unit})*{v}, 0)]` `VIEW[{dist_unit} ? "ft" : "m"]`/`VIEW[{time_unit} ? "round" : "s"]`

**Tempo de queda:** `VIEW[round(52.184894023/(9.81*(1+5*{time_unit})) * acosh(exp(9.81*{fall_dist}*(1-0.6952*{dist_unit})/(52.184894023^2))), 0)]` `VIEW[{time_unit} ? "round" : "s"]`

**Dano:** `VIEW[round(({v}/7.690899087747)^2, 0)]`d6

### Distância
**Tempo de queda:** `INPUT[number(class(nb-mb-css)):fall_time]` `VIEW[{time_unit} ? "rounds" : "s"]`

**Velocidade da queda:** `VIEW[round(52.184894023*(1+5*{time_unit})/(1-0.6952*{dist_unit})*tanh({fall_time}*(1+5*{time_unit})*9.81/52.184894023), 0)][:v2]` `VIEW[{dist_unit} ? "ft" : "m"]`/`VIEW[{time_unit} ? "rounds" : "s"]`

**Distância da queda:** `VIEW[(52.184894023)^2/9.81 * log(cosh(9.81*{fall_time}*(1+5*{time_unit})/52.184894023))][math(hidden):x]` `VIEW[round({x}/(1-0.6952*{dist_unit}), 0)]` `VIEW[{dist_unit} ? "ft" : "m"]` 

**Dano:** `VIEW[round(({v2}*(1-0.6952*{dist_unit})/(7.690899087747*(1+5*{time_unit})))^2, 0)]`d6 

## Queda ou descida consciente 

**Teste de acrobacia (destreza) contra a queda em pés.** 
Sucesso = Não sofre dano e não fica caída. 
Metade do DC = Metade do dano e Não fica caída.
Falha = Sofre dano total e fica caída.

**Altura:** `INPUT[number(class(nb-mb-css)):drop_dist]` `VIEW[{dist_unit} ? "ft" : "m"]`

**Rolagem de Acrobacia:** `INPUT[number(class(nb-mb-css)):acr]`

**DC:** `VIEW[round({drop_dist}/(0.3048+0.6952*{dist_unit}), 0)][:drop_DC]` | **DC metade:** `VIEW[round(1/2 * {drop_dist}/(0.3048+0.6952*{dist_unit}), 0)][:drop_DC_half]`

**Dano:** `VIEW[round(((52.184894023 * tanh(acosh(exp((9.81*{drop_dist}*(1-0.6952*{dist_unit}))/52.184894023^2))))/7.690899087747)^2, 0)][math(hidden):drop_dmg]` `VIEW[{acr} >= {drop_DC} ? "Sem dano" : {acr} >= {drop_DC_half} ? round({drop_dmg}/2, 0) : {drop_dmg}]`­`VIEW[{acr} < {drop_DC} ? "d6" : ""]`

**Prosa?** `VIEW[{acr} < {drop_DC_half} ? "Sim": "Não"]`


## Caída ou descida inconsciente
**Teste de Salvamento de Destreza contra a raiz quadrada de 10 vezes o dano de queda sofrido.** 
Sucesso = não fica caída. 
Falha = Fica caída.

**Dano de queda:** `INPUT[number(class(nb-mb-css)):fall_dmg]`

**Salvamento de Destreza:** `INPUT[number(class(nb-mb-css)):dex_save]`

**CD:** `VIEW[round(sqrt(10*{fall_dmg}), 0)]`

**Prosa?:** `VIEW[{dex_save} >= round(sqrt(10*{fall_dmg}), 0) ? "Não" : "Sim"]`

