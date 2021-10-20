---
layout: post
title:  "Introducing Count Dat Coin!"
date:   2021-10-19 20:15:00 -0400
permalink: /count-dat-coin/
---

## Calculating my Crypto Value

For a while I've used https://www.countmycrypto.com/ to loosely track the value of my
crypto holdings.

![countmycrypto.com](/assets/count_my_crypto.JPG)

I always felt a bit uneasy about it (as I with anything crypto-related). Is my data
being stored somewhere? Am I being tracked? Is anyone looking at this? It's hard 
_not_ to be paranoid when holding crypto. Unlike being reimbursed by your bank when
your credit card gets stolen, there's no one to save you when you get scammed out
of your crypto.

## Introducing Count Dat Coin

Ignoring the lame name :see_no_evil:, the `count-dat-coin` aims to put the user at ease
with respect data ownership and transparency.

1. The app does not use server-side storage of any kind - no postgres & not even redis.
2. The app is open source and can be reviewed by anyone.

## Current Status

As of writing, the app is deployed in Heroku at 
[https://count-dat-coin.herokuapp.com/](https://count-dat-coin.herokuapp.com/)

![count-dat-coin](/assets/count_dat_coin.JPG)

Crypto prices are fetched every 10 minutes from the CoinMarketCap API. The top 
10 cryptos by market cap value are supported. It's still bare-bones, but it
more or less gets the job done.

## Future Work

Listed by priority:

- Basic styling - including logos for each of the addedcryptos
- Add support for all cryptos listed on CoinMarketCap.com using an auto-complete styled
text box
- Change the name
- Register a custom domain