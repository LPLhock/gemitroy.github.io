---
description: Experimental
---

# Pair Trade

### 配对交易 - Bet on 2 correlated assets

#### Strategy A: 

Short the diverged up one and long the diverged down one

1. 获得近3个月内的D/12H数据
2. 计算 change percentage CP
3. 求close price协方差 \(coinA/coinB\)
4. 1. 找到大的正协方差 \(同向变化，CP同号概率大\)，
   2. 计算 CP\_B - CP\_A &gt; 0 的概率 P1
   3. 如果P1很大，long B，short A
   4. 如果P1很小，long A，short B
5. 1. 找到大的负协方差 \(反向变化，CP同号概率小\)
   2. 计算CP\_A + CP\_B &gt; 0 的概率 P2
   3. 如果P2很大，long A，long B
   4. 如果P2很小，short A，short B

```text
#!/bin/python

import csv
import operator
import sys
from decimal import Decimal
from itertools import combinations
import json
import argparse


import csv
import operator
import sys
from decimal import Decimal
from itertools import combinations
import json
import argparse


def main():
    parser = argparse.ArgumentParser()
    parser.add_argument("-f", type=str,help="The path to the coin list file", required=True)
    args = parser.parse_args()

    coin_list_file = args.f
    coin_pairs = getPairsFromCoinListFile(coin_list_file)

    for (coin_a, coin_b) in coin_pairs:
        print("calculating pair of " + coin_a + " and " + coin_b)
    
        #get candles of coin A and B
        if ("csv" in coin_list_file):
            list_a = getCandleListFromCsvFile(coin_a)
            list_b = getCandleListFromCsvFile(coin_b)
        else:
            list_a = getCandleListFromJsonFile(coin_a)
            list_b = getCandleListFromJsonFile(coin_b)
        print(list_a)
        print(list_b)

        total_count = len(list_a)
        print("Candle size: ",str(total_count))

        #price change percentage of coin A and B
        close_a, cp_a = getCloseAndCpFromCandleList(list_a)
        close_b, cp_b = getCloseAndCpFromCandleList(list_b)
        print("Price Change Percentage of ",coin_a)
        print(cp_a)
        print("Price Change Percentage of ",coin_b)
        print(cp_b)

        #positive cov, propability of situation 1 and 2
        positive_count = 0
        negative_count = 0
        for a,b in zip(cp_a, cp_b):
            if (b > a):
                positive_count += 1
            if (a + b > 0):                
                negative_count += 1
        p1 = int(positive_count * 100 / total_count)
        p2 = int(negative_count * 100 / total_count)
        print("Probalility of CP_B > CP_A: " + str(p1))
        print("Probalility of CP_A + CP_B > 0: " + str(p2))

        #covariance
        #cov_ab = cov(close_a, close_b)
        cov_ab = coPercentage(cp_a, cp_b)
        print("Covariance of A and B: " + str(cov_ab))

        #strategy suggestion
        strategy = applyStrategy(cov_ab, p1, p2, coin_a, coin_b)
        print("Suggested strategy is: ",strategy)

        #ouput result to file
        # btc-altcoin, cov, p1, p2, strategy
        result = coin_a,"-",coin_b,",",str(cov_ab),",",str(p1),",",str(p2),",",strategy,"\r\n"
        result = ''.join(result)
    
        f = open('result.txt', 'a+')
        f.write(result)

#cov function
def cov(x, y):
    mean_x = sum(x) / len(x)
    mean_y = sum(y) / len(y)
    covariance = sum((a - mean_x) * (b - mean_y) for (a,b) in zip(x,y)) / len(x)
    return int(covariance)

def coPercentage(x, y):
    same_sign_cnt = 0
    total_count = len(x)
    for a, b in zip(x, y):
        if (a==b | a*b > 0):
            same_sign_cnt += 1
    return same_sign_cnt * 100.0 / total_count

#input: time,open,high,low.close
def getCandleListFromCsvFile(candle_csv):
    with open('data/'+candle_csv) as csv_file:
        reader = csv.reader(csv_file)
        candle_list =  list(reader)
    return candle_list[1:]

#input: time,open,high,low.close,volumn,time,...
def getCandleListFromJsonFile(candle_json):
    with open('data/'+candle_json) as json_file:
        candle_list = json.load(json_file)
        return candle_list

#input: [time,open,high,low.close]
def getCloseAndCpFromCandleList(candles):
    change_percentage = []
    close_price = []
    for row in candles:
        pct = (float(row[4]) - float(row[1])) * 100.0 / float(row[1])
        change_percentage.append(round(pct, 2))
        close_price.append(float(row[4]))
    return close_price, change_percentage

#input: a,b,c
#output: [(a,b),(a,c),(b,c)]
def getPairsFromCoinListFile(filename):
    coins = [line.rstrip('\n') for line in open(filename)]
    pairs = combinations(coins, 2)
    return list(pairs)

def applyStrategy(cov_ab, pa, pb, coin_a, coin_b):
    strategy = "none"
    if (cov_ab > 60.0):
        if (pa >= 80.0):
            strategy = "long ",coin_b," / short ",coin_a
        if (pa <= 20.0):
            strategy = "long ",coin_a," / short ",coin_b
      
    if (cov_ab < 40.0):
        if (pb >= 80.0):
            strategy = "long ",coin_a," / long ",coin_b
        if (pb <= 20.0):
            strategy = "short ",coin_a," / short ",coin_b
    return ''.join(strategy)

if __name__ == '__main__':
    sys.exit(main())
```

#### Strategy B:

When 2 related assets are diverged, it will converge again

