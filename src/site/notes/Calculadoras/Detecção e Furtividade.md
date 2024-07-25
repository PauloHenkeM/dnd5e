---
{"dg-publish":true,"permalink":"/calculadoras/deteccao-e-furtividade/","title":"Calculadora de Detecção e Furtividade","created":"2024-07-25T07:50:01.736-03:00"}
---


###### Percepção do Detector: `INPUT[number(class(nb-mb-35)):spotterPerc]`
###### Percepção do Furtivo: `INPUT[number(class(nb-mb-35)):sneakerPerc]`

**Terreno:** `INPUT[inlineSelect(option(1, Terreno Plano Aberto), option(2, Terreno Aberto Difícil), option(3, Terreno Acidentado), option(4, Terreno Muito Acidentado)):terrain]`

**Vento:** `INPUT[inlineSelect(option(0, Calmo-Brisa Leve), option(1.5, Brisa Forte-Vendaval), option(3, Vendaval Forte-Tempestade Violenta)):wind]`

**Luz:** `INPUT[inlineSelect(option(0, Brilhante), option(2, Luz Fraca/Ligeiramente Obscuro), option(4, Escuridão/Altamente Obscuro)):light]` 

**Precipitação:** `INPUT[inlineSelect(option(0, Claro-Leve), option(1.5, Moderado-Considerável), option(3, Pesado-Muito Pesado)):rain]`

**Tamanho do Objeto:** `INPUT[inlineSelect(option(0.125, Minúsculo), option(0.25, Pequeno), option(0.5, Médio), option(1, Grande), option(2, Muito Grande), option(4, Enorme), option(8, Imenso), option(16, Colossal) ):size]`

#### Opções
- **Luneta?** `INPUT[toggle():spyglass]`
- **Invisível?** `INPUT[toggle():invisibility]`
- **Visão no Escuro?**  `INPUT[toggle():darkvision]`
- **Métrico?** `INPUT[toggle(offValue(1), onValue(0.3048)):metric]`{ #SpottingCalculator}


> [!check] Distância de Detecção: `VIEW[round({sizeFactor}*{penaltyFactor}*{func}*{metric})]` `VIEW[{metric} < 1 ? "mts" : "mts"]`
> `VIEW[100*{size}*({spyglass} ? 5/{terrain} : 1)][math(hidden):sizeFactor]` `VIEW[max(1, {light}+{wind}+{rain})][math(hidden):weather]` `VIEW[{weather}+6*{invisibility}-{darkvision}*{light}/2][math(hidden):penalties]` `VIEW[{spotterPerc}/({penalties}*{terrain})][math(hidden):penaltyFactor]` `VIEW[{sneakerPerc}-{spotterPerc} > 0 ? max(1.002876172*2*(1/(1+exp(0.2181959805*({sneakerPerc}-{spotterPerc})))-1/(1+exp(30*0.2181959805))), 0) : 1][math(hidden):func]`
