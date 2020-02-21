# Candle Volume Trade

## Strategy

Open long trade when positive candle and volume are higher than previous one

Close long trade when negative candle is lower and volume is higher than previous one

```text
#!/bin/python

import csv
import operator
import sys
from decimal import Decimal
from itertools import combinations
import json
import argparse
from datetime import datetime


def main():
    parser = argparse.ArgumentParser()
    parser.add_argument("-f", type=str,help="The path to the coin list file", required=True)
    args = parser.parse_args()

    coin_list_file = args.f
    coin_files = getCoinFilesFromListFile(coin_list_file)

    for coin_file in coin_files:
        # get candle of each coin
        candle_list = getCandleListFromJsonFile(coin_file)

        candle_size = len(candle_list)
        print(coin_file + " - Candle size: ",str(candle_size))

        # apply long strategy
        position_open_price_list = []
        position_close_price_list = []

        open_position = False

        for i in range(candle_size - 1):
            candle_a = candle_list[i]
            candle_b = candle_list[i+1]
            close_price_a = float(candle_a[4])
            close_price_b = float(candle_b[4])
            vol_a = float(candle_a[5])
            vol_b = float(candle_b[5])
            trade_time = datetime.fromtimestamp(candle_b[0]/1000)
            
            if (open_position == False):
                if (close_price_b > close_price_a and vol_b > vol_a):
                    open_position = True
                    position_open_price_list.append(close_price_b)
                    print(coin_file + " - Open long trade at price: " + str(close_price_b) + " at time: " + str(trade_time))
            if (open_position == True):
                if (close_price_b < close_price_a and vol_b > vol_a):
                    open_position = False
                    position_close_price_list.append(close_price_b)
                    print(coin_file + " - Close long trade at price: " + str(close_price_b) + " at time: " + str(trade_time))

        open_position_count = len(position_open_price_list)
        close_position_count = len(position_close_price_list)
        print(coin_file + " - Long open count: " + str(open_position_count))
        print(coin_file + " - Long close count: " + str(close_position_count))

        # summarize profit
        profit_sum = 0
        for i in range(close_position_count):
            profit_percentage = (position_close_price_list[i] - position_open_price_list[i]) / position_close_price_list[i]
            profit_sum += profit_percentage

        print(coin_file + " - Profit sum: " + str(profit_sum))
        # ouput result to file
        # coin_name, long_open_count,profit_sum
        result = coin_file,",",str(open_position_count),",",str(profit_sum),"\r\n"
        result = ''.join(result)
    
        f = open('result.txt', 'a+')
        f.write(result)

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

#get all coin files from a file list
def getCoinFilesFromListFile(coin_list_file):
    coin_files = [line.rstrip('\n') for line in open(coin_list_file)]
    return coin_files

if __name__ == '__main__':
    sys.exit(main())
```



