---
{"CoinsCopper":2000,"CoinsSiler":1,"CoinsElectrum":20,"CoinsGold":1,"CoinsPlatinum":100,"PartySize":4,"tags":["Calculadoras"],"created":"2024-07-24","dg-publish":true,"permalink":"/outros/calculadora-de-moeda/","dgPassFrontmatter":true}
---


# Quantidade

|Tipo|Entrada|Cobre|Prata|Electrum|Ouro|Platina|
|---|---|---|---|---|---|---|
|Cobre|`INPUT[number:CoinsCopper]`|`VIEW[{CoinsCopper}]`|`VIEW[{CoinsCopper}/10]`|`VIEW[{CoinsCopper}/50]`|`VIEW[{CoinsCopper}/100]`|`VIEW[{CoinsCopper}/1000]`|
|Prata|`INPUT[number:CoinsSiler]`|`VIEW[{CoinsSiler}*10]`|`VIEW[{CoinsSiler}]`|`VIEW[{CoinsSiler}/5]`|`VIEW[{CoinsSiler}/10]`|`VIEW[{CoinsSiler}/100]`|
|Electrum|`INPUT[number:CoinsElectrum]`|`VIEW[{CoinsElectrum}*50]`|`VIEW[{CoinsElectrum}*5]`|`VIEW[{CoinsElectrum}]`|`VIEW[{CoinsElectrum}/2]`|`VIEW[{CoinsElectrum}/20]`|
|Ouro|`INPUT[number:CoinsGold]`|`VIEW[{CoinsGold}*100]`|`VIEW[{CoinsGold}*10]`|`VIEW[{CoinsGold}*2]`|`VIEW[{CoinsGold}]`|`VIEW[{CoinsGold}/10]`|
|Platina|`INPUT[number:CoinsPlatinum]`|`VIEW[{CoinsPlatinum}*1000]`|`VIEW[{CoinsPlatinum}*100]`|`VIEW[{CoinsPlatinum}*20]`|`VIEW[{CoinsPlatinum}*10]`|`VIEW[{CoinsPlatinum}]`|


Tamanho do Grupo: `INPUT[number:PartySize]`

## Valor Total Convertido

|Tipo|Total|Total Por Jogador|
|---|---|---|
|Cobre|`VIEW[{CoinsCopper}+({CoinsSiler}*10)+({CoinsElectrum}*50)+({CoinsGold}*100)+({CoinsPlatinum}*1000)]`|`VIEW[({CoinsCopper}+({CoinsSiler}*10)+({CoinsElectrum}*50)+({CoinsGold}*100)+({CoinsPlatinum}*1000))/{PartySize}]`|
|Prata|`VIEW[(({CoinsCopper}+({CoinsSiler}*10)+({CoinsElectrum}*50)+({CoinsGold}*100)+({CoinsPlatinum}*1000))/10)]`|`VIEW[(({CoinsCopper}+({CoinsSiler}*10)+({CoinsElectrum}*50)+({CoinsGold}*100)+({CoinsPlatinum}*1000))/10)/{PartySize}]`|
|Electrum|`VIEW[(({CoinsCopper}+({CoinsSiler}*10)+({CoinsElectrum}*50)+({CoinsGold}*100)+({CoinsPlatinum}*1000))/50)]`|`VIEW[(({CoinsCopper}+({CoinsSiler}*10)+({CoinsElectrum}*50)+({CoinsGold}*100)+({CoinsPlatinum}*1000))/50)/{PartySize}]`|
|Ouro|`VIEW[(({CoinsCopper}+({CoinsSiler}*10)+({CoinsElectrum}*50)+({CoinsGold}*100)+({CoinsPlatinum}*1000))/100)]`|`VIEW[(({CoinsCopper}+({CoinsSiler}*10)+({CoinsElectrum}*50)+({CoinsGold}*100)+({CoinsPlatinum}*1000))/100)/{PartySize}]`|
|Platina|`VIEW[(({CoinsCopper}+({CoinsSiler}*10)+({CoinsElectrum}*50)+({CoinsGold}*100)+({CoinsPlatinum}*1000))/1000)]`|`VIEW[(({CoinsCopper}+({CoinsSiler}*10)+({CoinsElectrum}*50)+({CoinsGold}*100)+({CoinsPlatinum}*1000))/1000)/{PartySize}]`|



___
**Links para esta página**  
- [[Outros/Home\|Home]]