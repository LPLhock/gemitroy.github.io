# Strategy

### Turtle Trade

坚定策略

寻求概率优势

### Scalping

Sell almost immediately after a trade becomes profitable

### 拐点力学

### Pair Trade

Bet on 2 correlated asset convergence.

Short the diverged up one and long the diverged down one

Quantify:

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

import ms.version

def main():
    with open('ohlc/btc.csv', mode='r') as csv_a:
        reader_a = csv.reader(csv_a)
        list_a = list(reader_a)
    print(list_a)

    with open('ohlc/altcoin.csv', mode='r') as csv_b:
        reader_b = csv.reader(csv_b)
        list_b = list(reader_b)
    print(list_b)

    cp_a = []
    close_a = []
    for row in list_a[1:]:
        pct = (float(row[4]) - float(row[1])) * 100.0 / float(row[1])
        cp_a.append(round(pct, 2))
        close_a.append(float(row[4]))
    print(cp_a)

    cp_b = []
    close_b = []
    for row in list_b[1:]:
        pct = (float(row[4]) - float(row[1])) * 100.0 / float(row[1])
        cp_b.append(round(pct, 2))
        close_b.append(float(row[4]))
    print(cp_b)

    diff_ab = map(operator.sub, cp_a, cp_b)
    print(diff_ab)

    cov_ab = cov(close_a, close_b)
    print(cov_ab)

    # append to result.txt
    # btc-altcoin, cov, p1, p2

def cov(x, y):
    mean_x = sum(x) / len(x)
    mean_y = sum(y) / len(y)
    return sum((a - mean_x) * (b - mean_y) for (a,b) in zip(x,y)) / len(x)


if __name__ == '__main__':
    sys.exit(main())
```

### Stock/Index Arbitrage

### Commodity Diff Periods Arbitrage



### 经验

小止损，大盈利

入场时必须想好出场点和入场点

大周期和小周期策略应该有不同的止盈止损比率

分散仓位

## 

