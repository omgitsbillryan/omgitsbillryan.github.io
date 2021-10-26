---
layout: post
title:  "Introducing Count Dat Coin!"
date:   2021-10-19 20:15:00 -0400
permalink: /count-dat-coin/
---

## Calculating my Crypto Value

For a while I've used [https://www.countmycrypto.com](https://www.countmycrypto.com) to loosely track the value of my
crypto holdings. I always felt a bit uneasy about it (as I with anything crypto-related). 

- :fearful: **_Is my data being stored somewhere?_**
- :cold_sweat: **_Am I being tracked?_** 
- :scream: **_Is someone else looking at my data?_** 

It's hard _not_ to be paranoid when holding crypto. Unlike being reimbursed by your 
bank when your credit card gets stolen, no one is going to save you if & when you get 
scammed out of your crypto.

## Introducing Count Dat Coin

The aim is to put the user at ease with respect data ownership and transparency.

1. The app does not use server-side storage of any kind - no postgres & not even redis
2. The app is [open source and can be reviewed by anyone](https://github.com/omgitsbillryan/count-dat-coin)

## Current Status

The app is deployed in Heroku 
[https://count-dat-coin.herokuapp.com/](https://count-dat-coin.herokuapp.com/)

![count-dat-coin](/assets/count_dat_coin.JPG)

Crypto prices are fetched every 10 minutes from the CoinMarketCap API. The top 
10 cryptos by market cap value are supported.

## Future Work

- Basic styling - including logos for each of the addedcryptos
- Add support for all cryptos listed on CoinMarketCap.com using an auto-complete styled
text box
- Change the name
- Register a custom domain