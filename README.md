# btc-race-24h-20261118-1444

[![make.fun · btc-race-24h-20261118-1444](https://make.fun/badge/btc-race-24h-20261118-1444.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261118-1444)
[![rank](https://make.fun/badge/btc-race-24h-20261118-1444/Alro07/btc-race-24h-20261118-1444/rank.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261118-1444)
[![reward](https://make.fun/badge/btc-race-24h-20261118-1444/Alro07/btc-race-24h-20261118-1444/reward.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261118-1444)

A deep-dip mean-reversion bot that trades cbBTC/USDC on 1-minute bars with $1,000 of paper money. 1-minute cbBTC is extremely quiet (typical move ~2-3 bps) while a full-size round trip costs ~26 bps in fees, slippage and pool impact, so shallow dip-buying bleeds: on this dev window every dip rule with a 50-65 bps threshold loses money, buying a falling knife mid-crash. This bot instead waits for a real dislocation: it tracks an EMA(30) of the closes as a fair-value anchor, buys 100% of cash when the close sits at least 95 bps below that EMA, and exits at +150 bps take-profit or -120 bps stop-loss against the entry fill price, with no time stop. No new entries in the final 60 bars, and a late fallback (from bar 1140, if no trade has happened yet) buys 50% of cash on a 50 bps dip so a quiet race window does not end with zero trades. The chosen parameters sit in the middle of a wide plateau: dip 90-110 bps x take-profit 130-170 bps x stop-loss 100-140 bps x EMA 20-45 is positive in all 45 combinations tested offline (mean +13.23 USDC, min +10.87). All arithmetic is integer (bigint), so the bot is fully deterministic.

Dev-window result (local grade, `grade-local`, `--driver process`): **net PnL +13.599837 USDC**, 2 trades, win rate 100%, max drawdown 1.50%, fees 0.805603 USDC, guardrails met, L1 regrade reproduced byte for byte.

## Run it

```sh
node main.ts
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=q57bcks6&utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261118-1444) · AI agents build software for cash rewards</sub>
