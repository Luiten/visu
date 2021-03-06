# futuremaker 비주얼라이저

## 1. Binance UDF 확인

aws 에 이미 만들어둔 API를 사용한다.  

http://13.124.177.37:8080

테스트: http://13.124.177.37:8080/symbols?symbol=BTCUSDT

만약 자신만의 udf 서버를 따로 띄우고 싶다면 아래를 참고한다.

https://github.com/bergusman/tradingview-udf-binance-node


## 2. mobile.html에 url 설정.

mobile.html 에는 이미 설정되어있다.

```
datafeed: new Datafeeds.UDFCompatibleDatafeed("http://13.124.177.37:8080")
symbol: 'BTCUSDT',
interval: '1h',
```

로컬에 http 서버를 띄워서 확인해본다.

```
$ npm install -g http-server
$ http-server -p 3000
```

http://localhost:3000/mobile.html 에 접근하면 차트를 확인할수 있다.



## 3. futuremaker의 트레이딩 결과json 표시 (1번 탭으로)

futuremaker-json/trade-EveryGo.json 을 사용.


## 4. 테이블 형식의 트레이딩 결과는 다른 탭으로 표시. (2번 탭으로)

상단에는 futuremaker-json/status-EveryGo.json 파일로 요약을 보여주고 하단에는 TABLE형식으로 trade-EveryGo.json을 보여준다.

## 기타

- 차트는 기본 1H을 보여주고 차트에서 변경할수 있게 한다.
- 인디케이터는 나중에 고려한다.


## 추가
futuremaker에서 생성된 status, trade json파일 시각화

## 사용방법

모듈설치

```
npm install 
```

config.json에서 status, trade 디렉토리 경로 설정

```
"tradeDir": "C:\\Projects\\visu\\futuremaker-json",
"statusDir": "C:\\Projects\\visu\\futuremaker-json",
```

실행
```
npm start
```

제공하는 URI

| URI | 설명 |
| --- | --- |
| / | status, trade 파일목록 조회 |
| /bots | Bot 목록 조회 |
| /bots/<명청> | bot 화면 ( ex: /bots/EveryGo ) |

