# Read Data
```Python
# Read commodity data
# -*- coding: utf-8 -*-
"""
Created on Mon Oct 17 20:20:08 2016

@author: lshang
"""
FIELDNAME = ('tradingDay'
             , 'instrumentID', 'exchangeID', 'exchangeInstID'
             , 'lastPrice'
             , 'preSettlementPrice', 'preClosePrice', 'preOpenInterest'
             , 'openPrice', 'HighestPrice', 'lowestPrice'
             , 'volume', 'turnover', )

import struct

with open('a1707.data', mode='rb') as f:
    bs = f.read()
    i = 0
    while i < len(bs):
        tradingDay, instrumentID, exchangeID, exchangeInstID\
        , lastPrice, preSettlementPrice, preClosePrice, preOpenInterest\
        , openPrice, highestPrice, lowestPrice\
        , volume\
        , turnover, openInterest, closePrice, settlementPrice\
        , upperLimitPrice, lowerLimitPrice, preDelta, currDelta\
        , updateTime, updateMillisec\
        , bidPrice1, bidVolume1, askPrice1, askVolume1\
        , bidPrice2, bidVolume2, askPrice2, askVolume2\
        , bidPrice3, bidVolume3, askPrice3, askVolume3\
        , bidPrice4, bidVolume4, askPrice4, askVolume4\
        , bidPrice5, bidVolume5, askPrice5, askVolume5\
        , averagePrice = struct.unpack('9s31s9s31s7dI8d9sIdIdldIdldIdldIdldIdld', bs[i+0: i+392])
		
        print(tradingDay, instrumentID, exchangeID, exchangeInstID
              , lastPrice, preSettlementPrice, preClosePrice, preOpenInterest
              , volume, turnover, openInterest, closePrice, settlementPrice
              , upperLimitPrice, lowerLimitPrice, preDelta, currDelta
              , updateTime, updateMillisec
              , bidPrice1, bidVolume1, askPrice1, askVolume1
              , bidPrice2, bidVolume2, askPrice2, askVolume2
              , bidPrice3, bidVolume3, askPrice3, askVolume3
              , bidPrice4, bidVolume4, askPrice4, askVolume4
              , bidPrice5, bidVolume5, askPrice5, askVolume5
              , averagePrice, sep="\n")
        i += 392
```
