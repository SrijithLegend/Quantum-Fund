# Quantum Fund

## Overview

Quantum Fund is a rule-based intraday trading system designed to identify high-probability trend continuation opportunities in liquid equities. The system leverages volume-weighted price dynamics and directional strength filters to isolate structurally sound setups and generate execution-ready trade signals with defined risk parameters.

The architecture emphasizes deterministic logic over predictive modeling, focusing on market microstructure behavior rather than probabilistic price forecasting.

---

## Core Concept

The strategy is built around three primary principles:

* **Volume-Weighted Price Positioning**
  Uses VWAP as a dynamic intraday benchmark to determine institutional bias and fair value.

* **Directional Strength Filtering**
  Applies trend-strength metrics (e.g., ADX) to avoid low-momentum or range-bound environments.

* **Continuation-Based Entry Logic**
  Focuses on pullback → confirmation → continuation structures rather than early or anticipatory entries.

This combination enables the system to participate in sustained intraday moves while minimizing exposure to noise and false breakouts.

---

## Strategy Characteristics

| Attribute       | Description                               |
| --------------- | ----------------------------------------- |
| Strategy Type   | Intraday Trend Continuation               |
| Execution Style | Rule-based, deterministic                 |
| Signal Basis    | VWAP + Momentum + Price Structure         |
| Entry Mechanism | Breakout confirmation after pullback      |
| Risk Management | Pre-defined stop-loss and position sizing |
| Holding Period  | Intraday (no overnight exposure)          |

---

## System Architecture

```text
Quantum Fund/
│
├── Data/
│   └── data.py
│
├── Indicators/
│   ├── vwap_distance.py
│   ├── adx.py
│
├── Exit/
│   ├── atr_stoploss.py
│   ├── position_sizing.py
│
├── Backtesting/
│   └── backtesting.py
│
├── Screener/
│   └── screener.py
│
└── README.md
```

---

## Pipeline

```text
Market Data → Indicator Computation → Signal Filtering → Entry Trigger → Risk Allocation → Execution → Exit Logic
```

---

## Signal Framework

The system evaluates trade opportunities through a structured sequence:

1. **Market Condition Validation**

   * Sufficient liquidity (traded value threshold)
   * Active participation (volume-based filters)

2. **Trend Qualification**

   * Directional strength validation
   * Avoidance of low-volatility regimes

3. **Price Positioning**

   * Relative placement around VWAP
   * Identification of pullback zones

4. **Entry Confirmation**

   * Breakout of local structure
   * Momentum-based candle validation

5. **Risk Allocation**

   * Position sizing based on capital at risk
   * Stop-loss derived from volatility-adjusted levels

---

## Backtesting Engine

The backtesting framework is designed to simulate realistic intraday execution:

* Candle-by-candle simulation (5-minute resolution)
* Strict intraday exits (no overnight carry)
* Gap-aware stop-loss handling
* Trade-level logging with full lifecycle tracking
* Performance metrics:

  * Win rate
  * Profit factor
  * Expectancy
  * Maximum drawdown
  * Equity curve evolution

---

## Design Philosophy

Quantum Fund intentionally avoids:

* Overfitted indicator combinations
* Excessive parameter tuning
* Black-box predictive models
* Noise-sensitive signals

Instead, it prioritizes:

* Structural clarity
* Execution discipline
* Risk-first design
* Consistency over frequency

---

## Notes

* Core signal logic and parameter calibration are proprietary and not included in this repository.
* This project is intended for research, experimentation, and systematic trading development.

---

## Disclaimer

This project is for educational and research purposes only. It does not constitute financial advice or a recommendation to trade any financial instrument.
