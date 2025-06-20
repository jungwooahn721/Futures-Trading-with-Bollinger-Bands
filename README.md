> Name: **Jungwoo Ahn (안정우)**  
> Major: Computer Science & Mathematics  
> Student ID: 2021147584  

# Futures-Trading-with-Bollinger-Bands

Yahoo Finance에서 제공하는 NASDAQ-100(USD 선물) 데이터를 활용하여 Bollinger Band 기반의 간단한 정량적 트레이딩 전략을 구현했습니다.
코드 구성:
- Bollinger Bands, MACD, RSI 지표의 개념
- 해당 지표들을 활용한 매매 신호 생성 방법
- 기본적인 백테스트 시뮬레이션
- 전략의 수익성과 신호에 대한 시각화

This project demonstrates a simple quantitative trading strategy using **Bollinger Bands** on **NASDAQ-100 Futures (NQ=F)**. It includes:
- Technical indicator calculations (Bollinger Bands, MACD, RSI)
- Entry/exit signal generation based on indicator logic
- Backtest simulation to track portfolio performance
- Data visualization of signals, equity curve, and indicators


---

## 🧠 Motivation


저는 한때 해외 선물 거래에 관심을 가졌었고, 특히 NASDAQ-100(NAS100), 금(XAUUSD), 원유(USOUSD), 비트코인(BTCUSD)과 같은 상품들을 주로 거래해 보았습니다. 다양한 전략을 시도해본 결과, 그중에서 Bollinger Band 전략이 가장 직관적이고 제 성향에 가장 잘 맞는다고 느꼈습니다. 추세와 변동성을 함께 시각화해주기 때문에 매수·매도 시점을 명확하게 파악하는 데 도움이 되었고, 시장이 다양한 변동성 구간에서 어떻게 움직이는지를 이해하는 데 도움을 주었기 때문입니다. 이번 프로젝트는 그 당시의 관심을 다시 한번 데이터 기반, 프로그래밍적 관점에서 돌아보고, 실제 NAS100 선물 데이터를 통해 이 전략이 얼마나 효과적인지 백테스트해보는 기회가 되었습니다.

I chose this project because I was once very interested in futures trading—especially products like NASDAQ-100 (NAS100), gold (XAUUSD), crude oil (USOUSD), and Bitcoin (BTCUSD). Among many strategies I explored, the Bollinger Band strategy felt the most intuitive and well-suited to my trading style. I liked how it visualized both trend and volatility, giving me clearer signals for entry and exit. This project revisits that interest from a data-driven perspective by coding and backtesting it with actual NAS100 futures data.

---

## 📊 Strategy Overview

- **Bollinger Bands** are calculated with a 20-day moving average and ±2 standard deviations.
- A **Buy Signal** is generated when the price falls below the lower band.
- A **Sell Signal** is generated when the price rises above the upper band.
- **MACD** and **RSI** are included for signal confirmation.

---

##  Visualizations

### 1. Bollinger Bands with Buy/Sell Signals  
Shows how the price interacts with upper/lower bands and where entry/exit signals were triggered.

![Bollinger Bands](./images/bollinger_signals.png)

### 2. Portfolio Equity Curve  
Backtested performance starting from \$10,000 using the generated signals.

![Equity Curve](./images/equity_curve.png)

---


## Conclusion

첫 번째 차트인 Bollinger Band 및 매수/매도 신호 그래프를 보면, 전략이 국지적인 고점과 저점에서 비교적 잘 작동하는 모습을 확인할 수 있었습니다. 가격이 하단 밴드를 터치하거나 돌파한 직후 반등하는 구간에서 매수 신호가 발생하고, 상단 밴드를 돌파한 직후에는 매도 신호가 생성되어 단기 하락과 맞물리는 경우도 많았습니다. 하지만 추세장이 강하게 형성된 2021년과 2023년에는 상승 추세 중 매도 신호, 하락 추세 중 매수 신호가 잦게 발생해 오히려 손실로 이어질 가능성도 보였습니다. 이처럼 Bollinger Band는 **횡보장에서는 효과적**일 수 있으나, **추세장에서는 역추세 진입이 되어버리는 단점**도 함께 드러납니다.

두 번째 그래프인 수익곡선 (Equity, 잔고) 을 보면, 2020년~2021년 초반까지는 전략이 강한 상승 수익을 보였지만, 이후에는 수익이 정체되거나 오히려 일부 구간에서 손실이 나타나는 모습을 확인할 수 있습니다. 이는 전략이 특정 구간에 과적합되어 있었을 가능성 또는 리스크 관리(예: 손절 매커니즘, 포지션 크기 조절)의 부재를 시사합니다.

실시간 시장에 이 전략을 적용하려면 몇 가지 보완이 필요할 것 같습니다. 일단 단순한 진입/청산 신호만으로는 노이즈가 많기 때문에, **손절 조건**이나 **추세 확인 지표(MACD, RSI 등)** 와의 조합이 도움이 될 수 있습니다. **아주 적은 경험이지만 과거에 '기술적 분석의 종류/전략 보다는 감정에 휘둘리지 않는 손절/익절 기준의 설정과 이행이 훨씬 중요하구나' 라는 경험을 얻은 기억이 있습니다.** 또한 실제 시장에서는 부정확한 Bollinger Band, 체결 지연, 슬리피지(slippage) 등으로 인해 백테스트 결과만큼 수익을 낼 수 있을지는 확인해 보아야 알 것 같습니다. 이번 프로젝트를 통해 과거에 흥미를 가졌던 볼린저 밴드 보조지표를 이용한 해외 선물 트레이딩 전략을 정량적으로 검증해 볼 수 있었어서 유익했던 시간이었던 것 같습니다.


Looking at the first chart, which shows Bollinger Bands with buy/sell signals, the strategy appears to generate frequent trade entries that align reasonably well with local tops and bottoms. There are clear points where the price touches or crosses the lower band, triggering buy signals just before price rebounds, and similarly, sell signals near the upper band often precede a short-term decline. However, it's also visible that during strong trends—especially in 2021 and 2023—the strategy issues false counter-trend signals. This reflects one of the known weaknesses of Bollinger Bands: they tend to work better in **range-bound** markets than in **trending** ones.

The equity curve shows an aggressive growth phase early on, especially during the 2020–2021 period, but later becomes relatively flat with sudden drops, suggesting the strategy's performance became inconsistent. It might indicate overfitting to specific volatility patterns or the lack of a dynamic position-sizing method.

I think this strategy might work in live trading, but with several caveats. It would require better risk management, such as stop-loss logic and confirmation from other momentum indicators. Also, because live markets are noisy and fast-moving, execution delay and slippage can affect profitability. The backtest gave me insight into the strengths of this strategy in calm conditions, but in reality, combining Bollinger Bands with macro filters or news sentiment could enhance reliability. Overall, this was a valuable exercise in turning a manual strategy I once used into code—and seeing it work (and fail) visually taught me more than just reading about it ever could.



## 🛠️ Requirements

```bash
pip install pandas yfinance matplotlib
