# Read Data
```Python
# Read commodity data
# Read commodity data
# -*- coding: utf-8 -*-
"""
Created on Mon Oct 17 20:20:08 2016

@author: lshang
"""
FIELDNAME = ('tradingDay', 'instrumentID', 'exchangeID', 'exchangeInstID'
             , 'lastPrice', 'preSettlementPrice', 'preClosePrice', 'preOpenInterest'
             , 'openPrice', 'highestPrice', 'lowestPrice'
             , 'volume'
             , 'turnover', 'openInteresst', 'closePrice', 'settlementPrice'
             , 'upperLimitPrice', 'lowerLimitPrice', 'preDelta', 'currDelta'
             , 'updateTime', 'updateMillisec'
             , 'bidPrice1', 'bidVolume1', 'askPrice1', 'askVolume1'
             , 'bidPrice2', 'bidVolume2', 'askPrice2', 'askVolume2'
             , 'bidPrice3', 'bidVolume3', 'askPrice3', 'askVolume3'
             , 'bidPrice4', 'bidVolume4', 'askPrice4', 'askVolume4'
             , 'bidPrice5', 'bidVolume5', 'askPrice5', 'askVolume5'
             , 'averagePrice')

FIELDFMT  = ('9s', '31s', '9s', '31s'
             , 'd', 'd', 'd', 'd'
             , 'd', 'd', 'd'
             , 'I'
             , 'd', 'd', 'd', 'd'
             , 'd', 'd', 'd', 'd'
             , '9s', 'I'
             , 'd', 'I', 'd', 'I'
             , 'd', 'I', 'd', 'I'
             , 'd', 'I', 'd', 'I'
             , 'd', 'I', 'd', 'I'
             , 'd', 'I', 'd', 'I'
             , 'd')

def getFMT(style='@'):
    return style + ''.join(FIELDFMT)

import struct
LINESIZE = struct.calcsize(getFMT(''))

with open('a1611.data', mode='rb') as f:
    bs = f.read()

for i in range(int(len(bs)/LINESIZE)):
    values = struct.unpack(getFMT(), bs[i*LINESIZE:(i+1)*LINESIZE])
    print(values)
    
```
