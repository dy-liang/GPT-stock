# GPT-stock

`GPT-stock` is a Codex skill for short-term A-share stock trading analysis.
It is designed to identify the **5 Chinese A-share stocks with the highest expected profit probability within the next 1 trading week**, then provide an actionable trading plan for each stock.

## Version

`GPT-stock v1.0` is the foundation release.

## What This Skill Does

`GPT-stock` focuses on **current short-term swing trading opportunities** in the China A-share market.

It uses:

- public company filings and announcements,
- recent turnover and liquidity,
- valuation context such as PE,
- market heat and capital flow signals,
- upcoming domestic and international macro or industry events.

Based on these inputs, it returns the **top 5 short-term candidates** for the current one-week trading window.

## Default Output

For each of the 5 selected stocks, the skill provides:

- current reference price,
- buy point or buy zone,
- take-profit level,
- stop-loss level,
- position sizing ratio,
- core short-term trading logic.

It also includes:

- the actual trading window dates,
- key market risks for the week,
- source links used in the analysis.

## Default Assumptions

If the user does not provide extra constraints, `GPT-stock` assumes:

- market: `China A-shares`
- holding period: `next 5 trading days`
- style: `short-term swing trading`
- risk preference: `medium to moderately aggressive`
- allocation: `100% stock exposure`
- output language: same as the user

## How To Use

Example prompts:

```text
$GPT-stock
```

```text
Use $GPT-stock to find the 5 A-share stocks with the highest one-week profit probability and give buy points, take-profit levels, stop-loss levels, and position sizing.
```

```text
用 $GPT-stock 给我今天开始未来一周最值得做的5只A股，并直接给买点、止盈位、止损位和仓位比例。
```
## Typical Result Format

The output is usually presented as:

1. a short market summary,
2. a table of 5 stocks,
3. execution notes,
4. weekly risk notes,
5. source links.

Example table fields:

- 股票
- 当前参考价
- 买点
- 止盈位
- 止损位
- 仓位比例
- 核心逻辑

## Notes

- This skill is built for **time-sensitive** stock analysis, so it should use current web data rather than static memory.
- It is optimized for **one-week trading decisions**, not long-term value investing.
- Results are intended as an **actionable research output**, not guaranteed investment returns.

## Roadmap

Future updates may include:

- stronger sector rotation modeling,
- better event-driven scoring,
- clearer risk-tier modes,
- support for different trading styles,
- more refined portfolio allocation logic.

---
