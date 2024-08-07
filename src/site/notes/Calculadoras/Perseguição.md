---
{"dg-publish":true,"permalink":"/calculadoras/perseguicao/","title":"Calculadora de Perseguição","created":"2024-07-25T08:23:07.000-03:00","updated":"2024-07-25T23:46:07.000-03:00"}
---


**Dificuldade do Terreno:** `INPUT[inlineSelect(option(10, Ártico), option(10.00001, Desertos), option(5.00003, Campos Agrícolas), option(15, Floresta), option(5.00001, Pastagens), option(10.00002, Colinas), option(15.00001, Selva), option(5.00002, Prados), option(15.00003, Montanhas), option(15.00004, Mar Aberto), option(5, Estradas), option(20.00003, Mar Durante Tempestades), option(10.00003, Mar Perto da Costa), option(5.00004, Mar Perto da Costa Conhecida), option(20, Montanhas Íngremes), option(20.00001, Cosmologia Estranha), option(15.00002, Pântano), option(20.00002, Subterrâneo)):terrain]`

**Vento:** `INPUT[inlineSelect(option(0, Brisa-Calma), option(1.5, Brisa Forte-Vendaval), option(3, Tempestade-Vendaval Violento)):wind]`

**Luz:**  `INPUT[inlineSelect(option(0, Brilhante), option(2, Luz Difusa/Levemente Obscurecida), option(4, Escuridão/Altamente Obscurecida)):light]`

**Precipitação:** `INPUT[inlineSelect(option(0, Claro-Leve), option(1.5, Moderada-Substancial), option(3, Forte-Muito Forte)):rain]` `VIEW[max(1, {wind}+{light}+{rain})][math(hidden):weather]`

Vantagem inicial (mts) `INPUT[number(class(nb-mb-65)):QHeadstart_temp]` `VIEW[{QHeadstart_temp}*(1+2.28093*{metric})][math(hidden):QHeadstart]` 
Métrico? `INPUT[toggle:metric]` 

> [!note|clean no-t]
> | Descrição | Presa | Perseguidor |
> |-|-|-|
> | Velocidade Base | `INPUT[number(class(nb-mb-45)):QBaseSpeed]` mts | `INPUT[number(class(nb-mb-45)):PBaseSpeed]` mts
> | Teste de Sobrevivência | `INPUT[number(class(nb-mb-35)):QSurvival]` |  `INPUT[number(class(nb-mb-35)):PSurvival]`
> | Multiplicador de Veículo/Montaria | `INPUT[number(class(nb-mb-35)):QVm]`  | `INPUT[number(class(nb-mb-35)):PVm]` |
> | Velocidade Eficiente | `VIEW[round({QeffSpeed})]` mts `VIEW[{Qeff}*{QBaseSpeed}][math(hidden):QeffSpeed]` `VIEW[{QVm}/(8/7*2^(-({QSurvival}-({terrain}+{weather}))/10)+6/7)][math(hidden):Qeff]` | `VIEW[round({PeffSpeed})]` mts `VIEW[{Peff}*{PBaseSpeed}][math(hidden):PeffSpeed]` `VIEW[{PVm}/(8/7*2^(-({PSurvival}-({terrain}+{weather}))/10)+6/7)][math(hidden):Peff]` |

## Estado Final da Perseguição
**Velocidade Relativa:** `VIEW[round({RelSpeed}*(1-0.949212*{metric}), 1)]` `VIEW[{metric} ? "mts/s" : "mts"]` `VIEW[{Peff}*{PBaseSpeed}-{Qeff}*{QBaseSpeed}][math(hidden):RelSpeed]`

**Tempo para alcançar:** `VIEW[{RelSpeed} > 0 ? round({TtCu}) : "Infinito"]` `INPUT[inlineSelect(option(1, Segundos), option(6, Rounds), option(60, Minutos), option(3600, Horas), option(86400, Dias)):ChaseUnit]` `VIEW[{RelSpeed} > 0 ? 6*{QHeadstart}/({RelSpeed}*{ChaseUnit}) : "Perseguidor não está ganhando da Presa!"][math(hidden):TtCu]`

**Distância Percorrida:** `VIEW[{RelSpeed} > 0 ? concat(string(round({ChaseUnit}*{TtCu}*1.894*{PeffSpeed}*(1+0.609*{metric})/60000,2)), string({metric} ? " km" : " km")) : "Infinito "]`

## Gestão da Perseguição
**Tempo de Perseguição Decorrido:** `INPUT[number(class(nb-mb-55)):ChaseTime]` `INPUT[inlineSelect(option(1, Segundos), option(6, Rounds), option(60, Minutos), option(3600, Horas), option(86400, Dias)):ChaseUnit]`

**Distância Presa - Perseguidor:** `VIEW[{QeffSpeed} > {PeffSpeed} ? "Presa supera Perseguidor!" : {ChaseTime} < round({TtCu}) ? concat(string(round((1-0.6952*{metric})*({QHeadstart}-{RelSpeed}/6*{ChaseTime}*{ChaseUnit}))), string({metric} ? " mts" : " mts")) : "Alcançou a Presa"]`

**Mudança na Deslocação Relativa:** `VIEW[{QeffSpeed} > {PeffSpeed} ? "Presa supera Perseguidor!" : {ChaseTime} < round({TtCu}) ? concat(string(-round((1-0.6952*{metric})*{RelSpeed}/6*{ChaseUnit}*{ChaseTime})), string({metric} ? " mts" : " mts")) : "Alcançou a Presa!"]`

**Deslocação Média da Perseguição:** `VIEW[{QeffSpeed} > {PeffSpeed} ? "Presa supera Perseguidor!" : {ChaseTime} < round({TtCu}) ? concat(string(round((1-0.6952*{metric})/(12*(5280-4280*{metric}))*(6*{QHeadstart}+{ChaseTime}*{ChaseUnit}*({QeffSpeed} + {PeffSpeed})), 2)), string({metric} ? " km" : " km")) : "Alcançou a Presa!"]`
^ChaseCalculator