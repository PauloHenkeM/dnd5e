---
{"dg-publish":true,"permalink":"/calculadoras/viagem/","created":"2024-07-25T17:21:58.693-03:00"}
---


**Velocidade Base:** `INPUT[inlineSelect(option(30.001, Caminhando), option(50.001, Camelo), option(40.001, Burro), option(40.002, Mula), option(40.003, Cavalo de Tração), option(40.004, Elefante), option(40.005, Mastim), option(40.006, Moorbounder), option(40.007, Pônei), option(40.008, Rinoceronte), option(60.001, Cavalo de Montaria), option(40.009, Tigre Dente-de-Sabre), option(60.002, Cavalo de Guerra), option(20.001, Grifo [caminhando]), option(80.001, Grifo [voando]), option(40.010, Hipogrifo [caminhando]), option(60.003, Hipogrifo [voando]), option(60.004, Pégaso [caminhando]), option(90.001, Pégaso [voando]), option(20.002, Peryton [caminhando]), option(60.005, Peryton [voando]), option(50.002, Unicórnio), option(60.006, Peryton [voando]), option(50.003, Unicórnio), option(50.004, Vassoura Voadora), option(30.002, Vassoura Voadora [acima de 200 lbs]), option(80.002, Tapete Voador [3ft x 5ft]), option(60.007, Tapete Voador [4ft x 6ft]), option(40.011, Tapete Voador [5ft x 7ft]), option(30.003, Tapete Voador [6ft x 9ft]), option(300.001, Caminhada do Vento), option(50.005, Caldeirão Voador), option(30.004, Carroça puxada por Cavalos), option(30.005, Carroça puxada por PCs), option(40.012, PHB Galé), option(10.001, PHB Barco de Quilha), option(30.006, PHB Longship), option(15.001, PHB Barco a Remo), option(20.003, PHB Navio à Vela), option(25.001, PHB Navio de Guerra), option(50.006, GOS Navio à Vela), option(45.001, Balão de Batalha Aquisions Inc), option(15.003, Beholder Mecânico Aquisions Inc), option(200.001, Nave Aérea Lyrandar de Ebberon), option(100.001, Galeão Lyrandar de Ebberon), option(300.002, Trem Relâmpago Orien de Ebberon)):BaseSpeed]`

**Velocidade de Viagem:** `INPUT[inlineSelect(option(1, Ritmo Normal), option(1.333333, Ritmo Lento), option(0.666667, Ritmo Rápido), showcase):SpeedMultiplier]` 

**Velocidade de Bônus:** `INPUT[number:AdditionalBonus]`

**Sobrecarregado:** `INPUT[toggle:Encumbered]` (`VIEW[{Encumbered} ? -10: 0]`) 
**Ferraduras da Velocidade:** `INPUT[toggle:HorseshoesofSpeed]` (`VIEW[{HorseshoesofSpeed} ? 30: 0]`)

Horas de Viagem por Dia `INPUT[number:HoursPerDay]`

**Nível de Exaustão:** `INPUT[inlineSelect(option(0, 0 Sem exaustão), option(1, 1 Desvantagem em testes de habilidade), option(2, 2 Velocidade reduzida pela metade), option(3, 3 Desvantagem em jogadas de ataque e testes de resistência), option(4, 4 Pontos de vida máximos reduzidos pela metade), option(5, 5 Velocidade reduzida a 0), option(6, 6 Morte)):ExhaustionLevel]`

**Nova Velocidade Base:** `VIEW[round({BaseSpeed} / ({ExhaustionLevel} > 1 ? 2 : 1) + ({Encumbered} ? -10 : 0) + ({HorseshoesofSpeed} ? 30 : 0) + {AdditionalBonus},1)]` |

**Quilômetros a Viajar:** `INPUT[number:TravelDistance]`

> [!check] Dias de Viagem: `VIEW[round(({TravelDistance} * ({varMins}/(({BaseSpeed} / ({ExhaustionLevel} > 1 ? 2 : 1) + ({Encumbered} ? -10 : 0) + ({HorseshoesofSpeed} ? 30 : 0) + {AdditionalBonus}) / 10) * {SpeedMultiplier})) / 60 / {HoursPerDay}, 1)]`

##### Observação: Viajando Mais de 8 Horas por Dia
Requer testes de Constituição a cada hora após 8 horas:
- CD 11 na hora 9
- CD 12 na hora 10

Cada falha adiciona um nível de [[Outros/Exaustão\|Exaustão]].

### Serviços de Transporte
**Nível de Perigo:** `INPUT[inlineSelect(option(1.5, Rota Segura), option(2, Chance de Bandidos), option(3, Terras Hostis), option(5, Zona de Guerra)):DangerLevel]`

**Rota Familiar** `INPUT[toggle:FamiliarRoute]`

**Membros do Grupo:** `INPUT[number:PartyMembers]`

**Estilo de Vida:** `INPUT[inlineSelect(option(0, Wretched), option(1, Squalid), option(2, Poor), option(10, Modest), option(20, Comfortable), option(40, Wealthy), option(100, Aristocratic)):LifestyleCostSP]`

**Incluir Refeições:** `INPUT[toggle:IncludeMeals]` `VIEW[round(({IncludeMeals} ? 1 : 0)*(({LifestyleCostSP}/10)*{PartyMembers})*round(({TravelDistance} * ({varMins}/(({BaseSpeed} / ({ExhaustionLevel} > 1 ? 2 : 1) + ({Encumbered} ? -10 : 0) + ({HorseshoesofSpeed} ? 30 : 0) + {AdditionalBonus}) / 10) * {SpeedMultiplier})) / 60 / {HoursPerDay}),1)]`gp.

| Service | Cost Per Mile (cp.) | Total Cost gp.cp |
|-|-|-|
| Carroça (entre cidades) | `INPUT[number:CoachCostPerM]` | `VIEW[round({TravelDistance}*({CoachCostPerM}*({DangerLevel}+({FamiliarRoute} ? -0.5 : 0))*{PartyMembers}),0)/100+(({IncludeMeals} ? 1 : 0)*(({LifestyleCostSP}/10)*{PartyMembers})*round(({TravelDistance} * ({varMins}/(({BaseSpeed} / ({ExhaustionLevel} > 1 ? 2 : 1) + ({Encumbered} ? -10 : 0) + ({HorseshoesofSpeed} ? 30 : 0) + {AdditionalBonus}) / 10) * {SpeedMultiplier})) / 60 / {HoursPerDay}))]`gp. |
| Carroça (dentro da cidade)   | `INPUT[number:CoachCost]` | `VIEW[round(({CoachCost}*({DangerLevel}+({FamiliarRoute} ? -0.5 : 0))*{PartyMembers}),0)/100]`gp.          |
| Enviar Mensageiro | `INPUT[number:MessengerCostPerM]` | `VIEW[round({TravelDistance}*({MessengerCostPerM}*({DangerLevel}+({FamiliarRoute} ? -0.5 : 0))),0)/100]`gp.           |
| Passagem de Navio | `INPUT[number:ShipCostPerM]` | `VIEW[round({TravelDistance}*({ShipCostPerM}*({DangerLevel}+({FamiliarRoute} ? -0.5 : 0))*{PartyMembers}),0)/100+(({IncludeMeals} ? 1 : 0)*(({LifestyleCostSP}/10)*{PartyMembers})*round(({TravelDistance} * ({varMins}/(({BaseSpeed} / ({ExhaustionLevel} > 1 ? 2 : 1) + ({Encumbered} ? -10 : 0) + ({HorseshoesofSpeed} ? 30 : 0) + {AdditionalBonus}) / 10) * {SpeedMultiplier})) / 60 / {HoursPerDay}))]`gp. |

> [!check] Tempo de viagem 🕓: `VIEW[round((88* {Viagem#TravelCalc}) / 60 / {Viagem#HoursPerDay}, 1)]`

> [!warning|clean no-t]- Cálculo
> **Travel Calc:** `VIEW[({Viagem#varMins}/(({Viagem#BaseSpeed} / ({Viagem#ExhaustionLevel} > 1 ? 2 : 1) + ({Viagem#Encumbered} ? -10 : 0) + ({Viagem#HorseshoesofSpeed} ? 30 : 0) + {Viagem#AdditionalBonus}) / 10) * {Viagem#SpeedMultiplier})][math:TravelCalc]`

