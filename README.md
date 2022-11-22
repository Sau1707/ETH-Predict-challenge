# ETH-Predict-challenge

See [Ocean reposity](https://github.com/oceanprotocol/predict-eth) for all the details

## Goal
The goal of the challenge it's to predict as close as possible the [ETH](https://ethereum.org/it/) price for each hour up to 12h in the future.
The judges will look ad the following hours for the results:
```
Prediction at times: Dec 12, 2022 at 1:00 UTC, 2:00, ..., 12:00 (12 predictions total)
```
Click [here](https://github.com/oceanprotocol/predict-eth/blob/main/challenges/main2.md#appendix-what-judges-will-do) to see how it will be judged

## Approach
Since it's impossible to know the perfect model in advance and what factor influence the price, the only solution it's to try a lot of diffrent methods and brute force to find the best one.

The program will then run 12h back in time. It will generate an AI model, and the dataset to train it. After the training it will be tested with the prices of the last 12h and the results as well the accuracy will the set in a json format:
```js
{
    "r2_score": "%", // to maximaze
    "calc_nmse": number, // to minimaze
    "starting-time": "AAAA-MM-GG HH-MM-SS", 
    "results": [] // array with the 12 prediction
    "target": [] // array with the 12 target
    
}
```

Some parameters that can be used, they maybe have a relations:

a) [technical state of network](https://levelup.gitconnected.com/measuring-the-influence-of-on-chain-metrics-on-ethereum-price-81b7633be832) \
Both ETH and BTC can have an influence
  1) Tokens supply
  2) Active Addresses
  3) Transactions number
  4) ETH 2.0 staked 
  
b) [Integration of market metrics](https://levelup.gitconnected.com/measuring-the-influence-of-on-chain-metrics-on-ethereum-price-81b7633be832) \
  1) Exchange reserve in ETH, BTC and USD
  2) Estimated leverage ratio
  3) Open interest
  
c) [Others market](https://finance.yahoo.com/)
  1) Related to tecnologies (AAPL, TSLA, META, AMZN, ..)
  2) Raw materials (GOLD, SILVER, ...)
  
d) World events \
This are a bit harder to get the data. An approch it's to use an ai to see if the text it's positive or negative
  1) Natural disaster (floods, earthquakes, ...)
  2) Man related events (war, election, ...)
  3) Bullshit (celebrities, trends, ...)
