---
{"dg-publish":true,"permalink":"/calculadoras/moedas/","title":"Calculadora de Moedas","created":"2024-07-25T09:31:59.000-03:00","updated":"2024-07-25T23:45:15.000-03:00"}
---

## Entrada

**Tamanho do Grupo** `INPUT[number(class(nb-mb-css)):PartySize]`
**Métrico?** `INPUT[toggle(offValue(1), onValue(0.4536)):metric]`

- **Prata:** `INPUT[number(class(nb-mb-css)):CoinsSilver]`
- **Electrum:** `INPUT[number(class(nb-mb-css)):CoinsElectrum]`
- **Ouro:** `INPUT[number(class(nb-mb-css)):CoinsGold]`
- **Platina:** `INPUT[number(class(nb-mb-css)):CoinsPlatinum]`
- **Adamantina:** `INPUT[number(class(nb-mb-css)):CoinsAdamantine]`
- **Cobre:** `INPUT[number(class(nb-mb-css)):CoinsCopper]`

## Quantidade

> [!note | clean no-t] 
> ###### Tabela de Conversão
> | Tipo | Cobre | Prata | Electrum | Ouro | Platina | Adamantina |
> |-|:-:|:-:|:-:|:-:|:-:|:-:|
> | Cobre | `VIEW[{CoinsCopper}]` | `VIEW[{CoinsCopper}/10]` | `VIEW[{CoinsCopper}/50]` | `VIEW[{CoinsCopper}/100]` | `VIEW[{CoinsCopper}/1000]` | `VIEW[{CoinsCopper}/10000]` |
> | Prata |  `VIEW[{CoinsSilver}*10]` | `VIEW[{CoinsSilver}]` | `VIEW[{CoinsSilver}/5]` | `VIEW[{CoinsSilver}/10]` | `VIEW[{CoinsSilver}/100]` | `VIEW[{CoinsSilver}/1000]` |
> | Electrum |  `VIEW[{CoinsElectrum}*50]` | `VIEW[{CoinsElectrum}*5]` | `VIEW[{CoinsElectrum}]` | `VIEW[{CoinsElectrum}/2]` | `VIEW[{CoinsElectrum}/20]`  | `VIEW[{CoinsElectrum}/200]` |
> | Ouro |    `VIEW[{CoinsGold}*100]` | `VIEW[{CoinsGold}*10]` | `VIEW[{CoinsGold}*2]` | `VIEW[{CoinsGold}]` | `VIEW[{CoinsGold}/10]` | `VIEW[{CoinsGold}/100]` |
> | Platina |  `VIEW[{CoinsPlatinum}*1000]` | `VIEW[{CoinsPlatinum}*100]` | `VIEW[{CoinsPlatinum}*20]` | `VIEW[{CoinsPlatinum}*10]` | `VIEW[{CoinsPlatinum}]` | `VIEW[{CoinsPlatinum}/10]` |
> | Adamantina |  `VIEW[{CoinsAdamantine}*10000]` | `VIEW[{CoinsAdamantine}*1000]` | `VIEW[{CoinsAdamantine}*200]` | `VIEW[{CoinsAdamantine}*100]` | `VIEW[{CoinsAdamantine}*10]` | `VIEW[{CoinsAdamantine}]` |

> [!note | clean no-t] 
> ###### Divisão do Dinheiro  
> | Denominação  | # | Total por Jogador |
> |-|:-:|:-:|
> | Cobre   | `VIEW[{amountCoin}]` | `VIEW[{amountCoin}/{PartySize}]` |
> | Prata   | `VIEW[round(0.1*{amountCoin}, 2)]` | `VIEW[round({amountCoin}/(10*{PartySize}), 2)]` |
> | Electrum | `VIEW[round(0.02*{amountCoin}, 2)]` | `VIEW[round({amountCoin}/(50*{PartySize}), 2)]` |
> | Ouro     | `VIEW[round(0.01*{amountCoin}, 2)]` | `VIEW[round({amountCoin}/(100*{PartySize}), 2)]` |
> | Platina | `VIEW[round(0.001*{amountCoin}, 2)]` | `VIEW[round({amountCoin}/(1000*{PartySize}), 2)]` |
> | Adamantina | `VIEW[round(0.0001*{amountCoin}, 2)]` | `VIEW[round({amountCoin}/(1000*{PartySize}), 2)]` |

`VIEW[{CoinsCopper}+({CoinsSilver}*10)+({CoinsElectrum}*50)+({CoinsGold}*100)+({CoinsPlatinum}*1000)+({CoinsAdamantine}*10000)][math(hidden):amountCoin]`
 
## Peso

> [!note | clean no-t] 
> ###### Tabela de Conversão
> | Denominação | Cobre | Prata | Electrum | Ouro | Platina | Adamantina |
> |-|:-:|:-:|:-:|:-:|:-:|:-:|
> | Cobre | `VIEW[round({metric}*{CoinsCopper}/50, 2)]` `VIEW[{unit}]` | `VIEW[round({metric}*{CoinsCopper}/500, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsCopper}/2500, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsCopper}/5000, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsCopper}/50000, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsCopper}/500000, 2)]` `VIEW[{unit}]`|
> | Prata |  `VIEW[round({metric}*{CoinsSilver}/5, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsSilver}/50, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsSilver}/250, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsSilver}/500, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsSilver}/5000, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsSilver}/50000, 2)]` `VIEW[{unit}]`|
> | Electrum |  `VIEW[round(10*{metric}*{CoinsElectrum}, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsElectrum}, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsElectrum}/50, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsElectrum}/100, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsElectrum}/1000, 2)]`  `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsElectrum}/10000, 2)]` `VIEW[{unit}]` |
> | Ouro | `VIEW[round(2*{metric}*{CoinsGold}, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsGold}/5, 2)]` `VIEW[{unit}]`| `VIEW[round(20*{metric}*{CoinsGold}/5, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsGold}/50, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsGold}/500, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsGold}/5000, 2)]` `VIEW[{unit}]`|
> | Platina |  `VIEW[round(20*{metric}*{CoinsPlatinum}, 2)]` `VIEW[{unit}]`| `VIEW[round(2*{metric}*{CoinsPlatinum}, 2)]` `VIEW[{unit}]`| `VIEW[round(200*{metric}*{CoinsPlatinum}/5, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsPlatinum}/5, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsPlatinum}/50, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsPlatinum}/500, 2)]` `VIEW[{unit}]` |
> | Adamantina |  `VIEW[round(200*{metric}*{CoinsAdamantine}, 2)]` `VIEW[{unit}]`| `VIEW[round(20*{metric}*{CoinsAdamantine}, 2)]` `VIEW[{unit}]`| `VIEW[round(2000*{metric}*{CoinsAdamantine}/5, 2)]` `VIEW[{unit}]`| `VIEW[round(2*{metric}*{CoinsAdamantine}, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsAdamantine}/5, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{CoinsAdamantine}/50, 2)]` `VIEW[{unit}]`|

> [!note | clean no-t]
> ###### Divisão do Dinheiro  
> | Denominação | Peso | Total por Jogador |
> |-|:-:|:-:|
> | Cobre   | `VIEW[round({metric}*{amountCoin}/50, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{amountCoin}/(50*{PartySize}), 2)]` `VIEW[{unit}]`|
> | Prata   | `VIEW[round({metric}*{amountCoin}/500, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{amountCoin}/(500*{PartySize}), 2)]` `VIEW[{unit}]`|
> | Electrum | `VIEW[round({metric}*{amountCoin}/2500, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{amountCoin}/(1000*{PartySize}), 2)]` `VIEW[{unit}]`|
> | Ouro     | `VIEW[round({metric}*{amountCoin}/5000, 2)]` `VIEW[{unit}]` | `VIEW[round({metric}*{amountCoin}/(5000*{PartySize}), 2)]` `VIEW[{unit}]`|
> | Platina | `VIEW[round({metric}*{amountCoin}/50000, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{amountCoin}/(50000*{PartySize}), 2)]` `VIEW[{unit}]`|
> | Adamantina | `VIEW[round({metric}*{amountCoin}/500000, 2)]` `VIEW[{unit}]`| `VIEW[round({metric}*{amountCoin}/(500000*{PartySize}), 2)]` `VIEW[{unit}]`|

`VIEW[{metric} < 1 ? "kg" : "lbs"][math(hidden):unit]`