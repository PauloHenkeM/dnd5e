---
{"dg-publish":true,"permalink":"/calculadoras/erro-de-teletransporte/","created":"2024-07-25T12:08:06.000-03:00","updated":"2024-08-07T16:28:38.053-03:00"}
---


A magia imprevisível da conjuração resulta em uma jornada difícil. Cada criatura teleportada (ou o objeto alvo) sofre `dice: 3d10` de dano de força, e o Mestre refaz a rolagem na tabela para ver onde você vai parar (múltiplos acidentes podem ocorrer, causando dano cada vez).

**Distância de Teleporte:** `INPUT[number():TP_dist]` `INPUT[inlineSelect(option(ft), option(m), option(km), option(miles), option(AU), option(ly), option(pc)):unit]`

**Familiaridade:** `INPUT[inlineSelect(option(7, Objeto Associado), option(6, Círculo Permanente), option(5, Muito Familiar), option(4, Visto Casualmente), option(3, Visto uma Vez), option(2, Descrição), option(1, Conceitual), option(0, Destino Falso)):fam]` 

**Rolagem:** `INPUT[number(class(nb-mb-css)):roll]`


| Resultado | Acidente | Área Semelhante | Fora do Alvo | No alvo |
|-|:-:|:-:|:-:|:-:|
| Objeto Associado /<BR />Círculo Permanente | | | | `VIEW[{fam} >= 6 ? "Yes": ""]` |
| Muito Familiar | `VIEW[{fam} == 5 & {roll} <= 5 ? "Yes": "" ]` | `VIEW[{fam} == 5 & {fam} >= 6 & {roll} <= 13 ? "Yes": "" ]` | `VIEW[{fam} == 5 & {roll} >= 14 & {roll} <= 24 ? round(random(1, 10)*random(1,10)*{TP_dist}/100, 2) : "" ]` `VIEW[{fam} == 5 & {roll} >= 14 & {roll} <= 24 ? {unit} : "" ]` | `VIEW[{fam} == 5 & {roll} >= 25 & {roll} <= 100 ? round({TP_dist}/100*((100-{roll})/(100-25))^2, 2) : "" ]` `VIEW[{fam} == 5 & {roll} >= 25 & {roll} <= 100 ? {unit} : "" ]` |
| Visto Casualmente | `VIEW[{fam} == 4 & {roll} <= 33 ? "Yes": "" ]` | `VIEW[{fam} == 4 & {roll} >= 34 & {roll} <= 43 ? "Yes": "" ]` | `VIEW[{fam} == 4 & {roll} >= 44 & {roll} <= 53 ? round(random(1, 10)*random(1,10)*{TP_dist}/100, 2) : "" ]` `VIEW[{fam} == 4 & {roll} >= 44 & {roll} <= 53 ? {unit} : "" ]` | `VIEW[{fam} == 4 & {roll} >= 54 & {roll} <= 100 ? round({TP_dist}/100*((100-{roll})/(100-54))^2, 2) : "" ]` `VIEW[{fam} == 4 & {roll} >= 54 & {roll} <= 100 ? {unit} : "" ]` |
| Visto uma Vez | `VIEW[{fam} == 3 & {roll} <= 43 ? "Yes": "" ]` | `VIEW[{fam} == 3 & {roll} >= 44 & {roll} <= 53 ? "Yes": "" ]` | `VIEW[{fam} == 3 & {roll} >= 54 & {roll} <= 73 ? round(random(1, 10)*random(1,10)*{TP_dist}/100, 2) : "" ]` `VIEW[{fam} == 3 & {roll} >= 54 & {roll} <= 73 ? {unit} : "" ]` | `VIEW[{fam} == 3 & {roll} >= 74 & {roll} <= 100 ? round({TP_dist}/100*((100-{roll})/(100-74))^2, 2) : "" ]` `VIEW[{fam} == 3 & {roll} >= 74 & {roll} <= 100 ? {unit} : "" ]` |
| Descrição | `VIEW[{fam} == 2 & {roll} <= 53 ? "Yes": "" ]` | `VIEW[{fam} == 2 & {roll} >= 54 & {roll} <= 63 ? "Yes": "" ]` | `VIEW[{fam} == 2 & {roll} >= 64 & {roll} <= 83 ? round(random(1, 10)*random(1,10)*{TP_dist}/100, 2) : "" ]` `VIEW[{fam} == 2 & {roll} >= 64 & {roll} <= 83 ? {unit} : "" ]` | `VIEW[{fam} == 2 & {roll} >= 84 & {roll} <= 100 ? round({TP_dist}/100*((100-{roll})/(100-84))^2, 2) : "" ]` `VIEW[{fam} == 2 & {roll} >= 84 & {roll} <= 100 ? {unit} : "" ]` |
| Conceitual | `VIEW[{fam} == 1 & {roll} <= 73 ? "Yes": "" ]` | `VIEW[{fam} == 1 & {roll} >= 74 & {roll} <= 79 ? "Yes": "" ]` | `VIEW[{fam} == 1 & {roll} >= 80 & {roll} <= 91 ? round(random(1, 10)*random(1,10)*{TP_dist}/100, 2) : "" ]` `VIEW[{fam} == 1 & {roll} >= 80 & {roll} <= 91 ? {unit} : "" ]` | `VIEW[{fam} == 1 & {roll} >= 92 & {roll} <= 100 ? round({TP_dist}/100*((100-{roll})/(100-95))^2, 2) : "" ]` `VIEW[{fam} == 1 & {roll} >= 92 & {roll} <= 100 ? {unit} : "" ]` |
| Destino Falso | `VIEW[{fam} == 0 & {roll} <= 50 ? "Yes": "" ]` | `VIEW[{fam} == 0 & {roll} >= 51 & {roll} <= 100 ? "Yes": "" ]` | | |

> [!warning|clean no-t]- Ângulo de Erro
>**O grupo acaba em:** `VIEW[{angle} >= 31 | {angle} < 1 ? "N": {angle} >= 1 & {angle} <= 3 ? "NNE" : {angle} >= 3 & {angle} <= 5 ? "NE" : {angle} >= 5 & {angle} <= 7 ? "ENE" : {angle} >= 7 & {angle} <= 9 ? "E" : {angle} >= 9 & {angle} <= 11 ? "ESE" : {angle} >= 11 & {angle} <= 13 ? "SE" : {angle} >= 13 & {angle} <= 15 ? "SSE" : {angle} >= 15 & {angle} <= 17 ? "S" : {angle} >= 17 & {angle} <= 19 ? "SSW" : {angle} >= 19 & {angle} <= 21 ? "SW" : {angle} >= 21 & {angle} <= 23 ? "WSW" : {angle} >= 23 & {angle} <= 25 ? "W" : {angle} >= 25 & {angle} <= 27 ? "WNW" : {angle} >= 27 & {angle} <= 29 ? "NV" : "NNV"]` (`VIEW[round(360*{angle}/32, 0)]`°) do alvo.
>**O alvo é:** `VIEW[{comp_angle} >= 31 | {comp_angle} < 1 ? "N": {comp_angle} >= 1 & {comp_angle} <= 3 ? "NNE" : {comp_angle} >= 3 & {comp_angle} <= 5 ? "NE" : {comp_angle} >= 5 & {comp_angle} <= 7 ? "ENE" : {comp_angle} >= 7 & {comp_angle} <= 9 ? "E" : {comp_angle} >= 9 & {comp_angle} <= 11 ? "ESE" : {comp_angle} >= 11 & {comp_angle} <= 13 ? "SE" : {comp_angle} >= 13 & {comp_angle} <= 15 ? "SSE" : {comp_angle} >= 15 & {comp_angle} <= 17 ? "S" : {comp_angle} >= 17 & {comp_angle} <= 19 ? "SSW" : {comp_angle} >= 19 & {comp_angle} <= 21 ? "SW" : {comp_angle} >= 21 & {comp_angle} <= 23 ? "WSW" : {comp_angle} >= 23 & {comp_angle} <= 25 ? "W" : {comp_angle} >= 25 & {comp_angle} <= 27 ? "WNW" : {comp_angle} >= 27 & {comp_angle} <= 29 ? "NV" : "NNV"]` (`VIEW[round(360*{comp_angle}/32, 0)]`°) dos jogadores.

`VIEW[{angle} >= 16 ? {angle}-16 : {angle}+16][math(hidden):comp_angle]`
`VIEW[random(0,32)][math(hidden):angle]`

