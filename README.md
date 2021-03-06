
# [Btrade API Document for Developer]
&nbsp;

### [API Info]


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Btrade provides an API for developers to help them develop a variety of apps and programs.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Now, with the API provided by Btrade, anyone can easily use features 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;such as user information, wallet information, orders,  trade history, and order cancellation.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;We also provide Wallet APIs to help build cryptocurrency-related services.


### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Generating an API Key](https://www.btrade.co.kr/mypage/mypage.do) (API Key can be generated from the __Btrade My page__.)


&nbsp;

---
&nbsp;
### [API Notice]
#### Open API Changes Guide
##### &nbsp;&nbsp;&nbsp; <Open API Changes>

&nbsp;&nbsp;&nbsp;The last trading information API(ticker) on the previous exchange has been deprecated,<br/>&nbsp;&nbsp;&nbsp;and a Ticker with market information has been added. 

&nbsp;

---

&nbsp;

### [INDEX]
### 1. Public API
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1-1. Ticker1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - Final trading information of Btrade Exchange <span style="color:red">(Deprecated)</span> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1-2. Ticker2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - Final trading information of Btrade Exchange (Added market information) <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1-3. Orderbook&nbsp; - Exchange's Sell / Buy order history info
 <br/>
### 2. Token
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2-1. Create&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - Initial Token Generation <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2-2. Refresh&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - Refreshing Access Token <br/>
### 3. Private API
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3-1. Account &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- View user's Info <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3-2. Balance &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- User Wallet Info <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3-3. Transaction - Trade History <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3-4. Cancel &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Cancel Open Orders (Sell / Buy) <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3-5. Place &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Place and Execute orders (Sell / Buy) <br/>
### 4. Status
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4-1. Token Error <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4-2. Exception <br/>

&nbsp;

---
&nbsp;
### [Reference]

### 1. Public API

#### 1-1. Ticker - Final trading information of Btrade Exchange <span style="color:red">(Deprecated)</span>

__[GET]__ &nbsp;&nbsp;&nbsp;```https://api.btrade.co.kr/api/ticker/currency/{coin_code}```

__[Curl]__ &nbsp;&nbsp;&nbsp;```curl -X GET --header 'Accept: application/json' 'https://api.btrade.co.kr/api/ticker/currency/{coin_code}'```

__[Response Body]__

```
{
  "status": "0000",
  "data": {
    "open_price": "10000",
    "close_price": "10000",
    "low": "10000",
    "high": "10000",
    "average_price": "0.0",
    "units_traded": "0E-18",
    "volume_1day": "0E-18",
    "volume_7day": "431.699880000000000000",
    "buy_price": "0000000000.00000000",
    "sell_price": "0000000000.00000000",
    "date": 1548933680756
  }
}
```

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|coin_code|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Coin Name (ALL, BTC, ETH, ETC, LTC, ZEC, etc.)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status: 0000|Normal|
|open_price|Opening price in last 24 hours|
|close_price|Closing price in last 24 hours|
|low|Lowest price in last 24 hours|
|High|Highest price in last 24 hours|
|average_price|Average price in last 24 hours|
|units_traded|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Currency trading volume in last 24 hours&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|volume_1day|Currency trading volume for the last 1 day|
|volume_7day|Currency trading volume for the last 7 days|
|buy_price|Highest buy price in pending orders|
|sell_price|Lowest sell price in pending orders|
|date|Current Timestamp|


&nbsp;
---
#### 1-2. Ticker - Final trading information of Btrade Exchange (Added market information)

__[GET]__ &nbsp;&nbsp;&nbsp;```https://api.btrade.co.kr/api/v1/ticker/currency/{coin_code}```

__[Curl]__ &nbsp;&nbsp;&nbsp;```curl -X GET --header 'Accept: application/json' 'https://api.btrade.co.kr/api/v1/ticker/currency/{coin_code}'```

__[Response Body]__

```
{
    "status": "0000",
    "data": {
        "KRW": {
            "open_price": "1000",
            "close_price": "10001000",
            "low": "1000",
            "high": "10003000",
            "average_price": "8594071.364285713",
            "units_traded": "6.014550000000000000",
            "volume_1day": "6.014550000000000000",
            "volume_7day": "30.019550000000000000",
            "buy_price": "0010001000.00000000",
            "sell_price": "0000000000.00000000",
            "date": 1564475297693
        },
        "BTC": {
            "open_price": "1.12345678",
            "close_price": "1.12345678",
            "low": "1.12345678",
            "high": "1.12345678",
            "average_price": "1.123456780000000000000000000000",
            "units_traded": "2.000000000000000000",
            "volume_1day": "2.000000000000000000",
            "volume_7day": "2.000000000000000000",
            "buy_price": "0000000001.12345678",
            "sell_price": "0000000000.00000000",
            "date": 1564475297863
        }
    }
}
```

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|coin_code|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Coin Name (ALL, BTC, ETH, ETC, LTC, ZEC, etc.)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status: 0000|Normal|
|open_price|Opening price in last 24 hours|
|close_price|Closing price in last 24 hours|
|low|Lowest price in last 24 hours|
|High|Highest price in last 24 hours|
|average_price|Average price in last 24 hours|
|units_traded|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Currency trading volume in last 24 hours&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|volume_1day|Currency trading volume for the last 1 day|
|volume_7day|Currency trading volume for the last 7 days|
|buy_price|Highest buy price in pending orders|
|sell_price|Lowest sell price in pending orders|
|date|Current Timestamp|

&nbsp;
---

#### 1-3. Orderbook - Exchange's Sell/Buy order history info

__[GET]__ &nbsp;&nbsp;&nbsp;```https://api.btrade.co.kr/api/orderbook/currency/{coin_code}```

__[Curl]__ &nbsp;&nbsp;&nbsp;```curl -X GET --header 'Accept: application/json' 'https://api.btrade.co.kr/api/orderbook/currency/{coin_code}'```


__[Response Body]__
````
{
  "status": "0000",
  "data": {
    "timestamp": 1548934145839,
    "order_currency": "BTC",
    "payment_currency": "KRW",
    "bids": [
      {
        "it_action": "buy",
        "it_market_cost": "0000000000.00000000",
        "nResCoin": "00000000.00000000"
      },
      {
        "it_action": "buy",
        "it_market_cost": "0000000000.00000000",
        "nResCoin": "00000000.00000000"
      },
    ],
    "asks": [
      {
        "it_action": "sell",
        "it_market_cost": "0000000000.00000000",
        "nResCoin": "00000000.00000000"
      },
      {
        "it_action": "sell",
        "it_market_cost": "0000000000.00000000",
        "nResCoin": "00000000.00000000"
      },
    ]
  }
}
````


__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|coin_code|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Coin Name (BTC, ETH, ETC, LTC, ZEC, etc.)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|timestamp|Current Time|
|order_currency|Coin|
|payment_currency|Payment Currency|
|it_action|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[bids]: buy / [asks]: sell&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|it_market_cost|Market Price|
|nResCoin|Available Coin|

&nbsp;

---
&nbsp;
### 2. Token

#### 2-1. Create - Initial Token Generation

__[POST]__ &nbsp;&nbsp;&nbsp;```https://api.btrade.co.kr/api/v1/access_token```

```
{
  "nonce":"1548998552194",
  "hstr":"54c25b135d6e80129b71e399fecf522016ab528be7459b1c33c73730de67fad6",
  "apikey":"BTkYXt3hv5BxzieKxHiE9zovAsDSVXraNpJ",
  "grant_type":"APIKEY",
  "expires_in":60
}
```

__[Curl]__

```
curl -X POST --header 'Content-Type: application/json;charset=UTF-8' --header 'Accept: application/json' -d '{ \ 
   "nonce":"1548998552194", \ 
   "hstr":"54c25b135d6e80129b71e399fecf522016ab528be7459b1c33c73730de67fad6", \ 
   "apikey":"BTkYXt3hv5BxzieKxHiE9zovAsDSVXraNpJ", \ 
   "grant_type":"APIKEY", \ 
   "expires_in":60 \ 
 }' 'https://api.btrade.co.kr/api/v1/access_token'
```

__[Response Body]__

```
{
  "status": "0000",
  "message": "success",
  "data": {
    "access_token": "fb2050d52602edd7798efff6fd7ed289a8d743a4bdda510e0aa374c50e3b2023",
    "access_token_expire": "1549002045865",
    "refresh_token": "48f9b90cee15348744b0da1a8e995c5d3833fd985d8f9dd138c04755b18731c7",
    "refresh_token_expire": "1551590445856"
  }
}
```

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|nonce|Request Time (Unix Time)|
|hstr|sha256( apikey + secretkey + nonce ) → Hex converted string|
|apikey|User API Key|
|grant_type|APIKEY|
|expires_in|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Access Token Access Token Expiration Time<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(Minute Time, min 30 minutes to max 60 minutes)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Response]__

|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status| 0000: Normal / others: error|
|message|Result Message|
|access_token|Access Token for Btrade API|
|access_token_expire|Access Token Expiration Time (Unix Time)|
|refresh_token|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Refresh Token to refresh your access tokenToken&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|refresh_token_expire|Refresh Token Expiration Time (Unix Time)|

&nbsp;
---

#### 2-2. Refresh - Refreshing Access Token

__[POST]__&nbsp;&nbsp;&nbsp;```https://api.btrade.co.kr/api/v1/access_token```

```
{
  "refresh_token":"48f9b90cee15348744b0da1a8e995c5d3833fd985d8f9dd138c04755b18731c7", 
  "expires_in":60, 
  "grant_type":"REFRESH"
}
```

__[Curl]__

```
curl -X POST --header 'Content-Type: application/json;charset=UTF-8' --header 'Accept: application/json' -d '{ \ 
   "refresh_token": "48f9b90cee15348744b0da1a8e995c5d3833fd985d8f9dd138c04755b18731c7", \ 
   "expires_in":60, \ 
   "grant_type":"REFRESH" \ 
 }' 'https://api.btrade.co.kr/api/v1/access_token'
```

__[Response Body]__

```
{
  "status": "0000",
  "message": "success",
  "data": {
    "access_token": "fb2050d52602edd7798efff6fd7ed289a8d743a4bdda510e0aa374c50e3b2023",
    "access_token_expire": "1549002045865",
    "refresh_token": "48f9b90cee15348744b0da1a8e995c5d3833fd985d8f9dd138c04755b18731c7",
    "refresh_token_expire": "1551590445856"
  }
}
```

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|refresh_token|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Refresh Token generated by Token Create API&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|expires_in|Access Token Expiration Time (Minute Time, min 30 minutes to max 60 minutes)|
|grant_type|REFRESH|

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status|0000: Normal / others: error|
|message| Result Message|
|access_token|Access Token for Btrade API|
|access_token_expire|Access Token Expiration Time (Unix Time)|
|refresh_token|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Refresh Token to refresh your access token&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|refresh_token_expire|Refresh Token Expiration Time (Unix Time)|

&nbsp;

---
&nbsp;
### 3. Private API

#### 3-1. Account - View user's Info

__[GET]__ &nbsp;&nbsp;&nbsp;```https://api.btrade.co.kr/api/private/v1/account?currency={currency}```

__[Curl]__

```
curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer 125543745d3c2712529a579d1383e89469e3cc9601cd08f22e4dd6c482b5d7b9' 'https://api.btrade.co.kr/api/private/v1/account?currency=BTC'
```

__[Response Body]__

```
{
  "status": "0000",
  "data": {
    "account_id": 3,
    "balance": 5532123.7132,
    "trade_fee": 0.005,
    "created": 1521439134000
  }
}
```

__[Input Header]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|Authorization|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Access Token&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|currency|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Coin Name (BTC, ETH, ETC, LTC, ZEC, etc.)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|



__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status|0000: Normal / others: error|
|account_id|User Unique Number|
|balance|Remaining Coin|
|trade_fee|Applied Fee Rate|
|created|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Join Time (Unix Time)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

&nbsp;
---
#### 3-2. Balance - User Wallet Info

__[GET]__ &nbsp;&nbsp;&nbsp;```https://api.btrade.co.kr/api/private/v1/balance?currency={currency}```

__[Curl]__

```
curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer 7488eeb56b924e369c2d60f738e795072d3e90740339dc42205f50743619cfb4' 'https://api.btrade.co.kr/api/private/v1/balance?currency=BTC'
```

__[Response Body]__

```
{
  "status": "0000",
  "data": {
    "total_krw": 9999613666.0878,
    "in_use_krw": 7598430736.27575,
    "available_krw": 2401182929.81205,
    "total_btc": 5532121.7132,
    "in_use_btc": 8.8742,
    "available_btc": 5532112.839
  }
}
```

__[Input Header]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|Authorization|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Access Token&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|currency|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Coin Name (ALL, BTC, ETH, ETC, LTC, ZEC, etc.)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status|0000: Normal / others: error|
|total_{currency}|Total Currency|
|in_use_{currency}|Currency in Use|
|available_{currency}|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Available Currency&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

&nbsp;
---

#### 3-3. Transaction - Trade History

__[GET]__ 

```
https://api.btrade.co.kr/api/private/v1/transaction?currency={currency}&deal_status={deal_status}&trd_state={trd_state}
```

__[Curl]__

```
curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer 7488eeb56b924e369c2d60f738e795072d3e90740339dc42205f50743619cfb4' 'https://api.btrade.co.kr/api/private/v1/transaction?currency=BTC&deal_status=0&trd_state=OK'
```

__[Response Body]__

```
{
  "status": "0000",
  "data": [
    {
      "search": 0,
      "orderId": "1901251726297700000003",
      "price": 3905.5,
      "trd_state": "OK",
      "fee": 0.0015,
      "trd_type": "BUY",
      "units": 0.001,
      "transfer_date": 1548404789817,
      "btc1krw": 3905500
    },
    {
      "search": 0,
      "orderId": "1901151956097700000003",
      "price": 41636.34,
      "trd_state": "OK",
      "fee": 0.005,
      "trd_type": "SELL",
      "units": 0.01019,
      "transfer_date": 1547549769770,
      "btc1krw": 4086000
    },
    {
      "search": 0,
      "orderId": "1901151956026220000003",
      "price": 44828.905,
      "trd_state": "OK",
      "fee": 0.005,
      "trd_type": "SELL",
      "units": 0.01097,
      "transfer_date": 1547549762618,
      "btc1krw": 4086500
    },
    ...
```

__[Input Header]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|Authorization|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Access Token&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|


__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|currency|Coin Name (BTC, ETH, ETC, LTC, ZEC, etc.)|
|deal_status|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Status - 0 (total), 1 (sell), 2 (buy), 3 (cancel), 4 (correct)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|trd_status|Order Status - OK, WAIT|

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status|0000: Normal / others: error|
|search|0 (total), 1 (sell), 2 (buy), 3 (deposit), 4 (withdraw)|
|orderId|Order Number|
|price|Trading Amount|
|trd_state|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Order Status (OK:Total executed, WAIT:Trading in Progress)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|fee|Trading Fee|
|trd_type|Status (BUY: Sell, SELL: Buy, C: Cancel, M: Correct)|
|units|Trade Currency Amount|
|transfer_date|Trading Date|
|{currency}1krw|Usual Market Price|

&nbsp;
---

#### 3-4. Cancel - Cancel Open Orders (Sell/Buy). 

__[POST]__&nbsp;&nbsp;&nbsp;``https://api.btrade.co.kr/api/private/v1/order/cancel``

```
{
  "currency" : "BTC",
  "org_ord_no" : "190208154943577"
}
```

__[Curl]__

```
curl -X POST --header 'Content-Type: application/json;charset=UTF-8' --header 'Accept: application/json' --header 'Authorization: Bearer 7603c80ddcd596c6fffb642e44470b9cea0d79e2e67a7b9de9ff5b957d46c1c7' -d '{ \ 
   "currency" : "BTC", \ 
   "org_ord_no" : "190208154943577" \ 
 }' 'https://api.btrade.co.kr/api/private/v1/order/cancel'
``` 

__[Response Body]__

```
{
  "status": "0000",
  "data": "Success"
}
```

__[Input Header]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|Authorization|Access Token|
|Content-Type|The Content-Type entity header is used to indicate the media type of the resource.<br/>(application/json;charset=UTF-8)

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|apikey|User API Unique Key|
|currency|Coin Name (BTC, ETH, ETC, LTC, ZEC, etc.)|
|org_ord_no|Order Number|
|nonce|Current Date (ex: 20190208)|
|hstr|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sha-256(nonce, currency, secretKey, sheckSum)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0000: Normal / others: error&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

&nbsp;
---

### 3-5. Place - Place and Execute orders (Sell/Buy).

__[POST]__&nbsp;&nbsp;&nbsp;``https://api.btrade.co.kr/api/private/v1/order/place``

```
{
  "currency" : "BTC",
  "deal_type" : "B",
  "deal_money" : "10000",
  "amount" : "1",
  "fee_type" : "K"
}
```

__[Curl]__

```
curl -X POST --header 'Content-Type: application/json;charset=UTF-8' --header 'Accept: application/json' --header 'Authorization: Bearer 7603c80ddcd596c6fffb642e44470b9cea0d79e2e67a7b9de9ff5b957d46c1c7' -d '{ \ 
   "currency" : "BTC", \ 
   "deal_type" : "B", \ 
   "deal_money" : "10000", \ 
   "amount" : "1", \ 
   "fee_type" : "K" \ 
 }' 'https://api.btrade.co.kr/api/private/v1/order/place'
```

__[Response Body]__

```
{
  "status": "0000",
  "data": "Success",
  "order_id": "1902081549435770000003"
}
```

__[Input Header]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|Authorization|Access Token|
|Content-Type|The Content-Type entity header is used to indicate the media type of the resource.<br/>(application/json;charset=UTF-8)


__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|currency|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Coin Name (BTC, ETH, ETC, LTC, ZEC, etc.)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|deal_type|Type of trade (B-Buy, S-Sell)|
|deal_money|Order Price|
|amount|Order Amount|
|fee_type|Fee Type (K-KRW Fee, C-Coin Fee) <br>* Only KRW fee is available when selling. |

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status| 0000: Normal / others: error|
|order_id|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Order Number&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

&nbsp;

---
&nbsp;

### Status

#### 4-1. Token Error

|&nbsp;&nbsp;&nbsp;Status Value&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|2001|Member api key is not exist.|
|2002|INCONSISTENCY HSTR|
|2003|Refresh Token is not exist.|
|2004|Access Token is not exist or expired.|
|2005|No Access Token in Header.|
|2006|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;IP information has changed. Again create_access_token api call.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|2007|MEMBER_API_KEY is disabled.|
|2008|MEMBER API is not authorized.|
|2009|MEMBER API is not allow ip.|

&nbsp;
---

#### 4-2. Exception

|&nbsp;&nbsp;&nbsp;Status Value&nbsp;&nbsp;&nbsp;|Description| 
|:------------:|:---------:|
|0001|Wrong currency entered|
|0002|Order id is not exist|
|0003|Price is not correct / Your order price is less than minimum price. (1,000 KRW)|
|0006|Amount is not correct / Your order amount is exceeded maximum amount<br/> / Trading unit is not correct / It is already registered to cancel the entire list.|
|1001|Invalid Parameter|
|1004|The data does not exist.|
|2000|No data|
|3000|Order State Ready|
|9999|Interval Server Error|