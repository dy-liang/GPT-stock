---
name: GPT-stock
description: Find the 5 Chinese A-share stocks with the highest expected profit probability for the current short-term one-week trading window, then provide concrete buy zones, take-profit levels, stop-loss levels, and position sizing. Use when the user asks for current A-share short-term picks, weekly swing trades, one-week stock ideas, buy/sell plans, stop-loss or take-profit levels, or wants a direct actionable shortlist based on public filings, turnover, valuation, capital flows, and upcoming domestic or international events.
---
# GPT-stock

## Overview

Use this skill to produce a current, actionable A-share short-term trading plan for the next 5 trading days.
The default deliverable is exactly 5 stocks plus concrete trade levels: buy point, take-profit, stop-loss, and position ratio.

## Hard Rules

1. Always browse for current data before answering. Do not rely on memory for prices, events, regulations, or company status.
2. Treat this as time-sensitive financial analysis. Use explicit calendar dates such as `2026-05-25` rather than only saying "today" or "next week".
3. Focus on `China A-shares` unless the user explicitly asks for Hong Kong, US, ETFs, funds, or futures.
4. Optimize for a `one-week trading window`, not long-term intrinsic valuation.
5. Do not give a generic watchlist. End with the single best 5-stock list.
6. If the market is closed on part of the period, state the actual tradable dates.

## Default Assumptions

If the user just says to use this skill and gives no extra constraints, assume:

1. the market is `China A-shares`,
2. the holding period is the next `5 trading days`,
3. the style is `short-term swing trading`,
4. the risk preference is `medium to moderately aggressive`,
5. the total suggested stock allocation is `100%`,
6. the response language should follow the user's language.

## Required Inputs To Build The Weekly View

Collect enough current information to support a short-term decision:

1. Latest prices, recent highs/lows, turnover, and liquidity for candidate stocks.
2. Recent company public information:
   - latest quarterly report or earnings update,
   - major announcements,
   - capital operations such as share transfers, inquiry transfers, unlocks, or buybacks.
3. Current market style and sector heat:
   - turnover leaders,
   - northbound or major-fund activity when available,
   - sector-level capital concentration.
4. This week's known catalysts:
   - China macro data,
   - overseas macro data,
   - earnings for globally relevant companies,
   - index review or rebalancing dates,
   - industry conferences or policy meetings.

## Preferred Source Order

Use primary or near-primary sources first:

1. Company filings and exchange pages:
   - `cninfo.com.cn`
   - `sse.com.cn`
   - `szse.cn`
   - official investor relations pages
2. Official macro calendars:
   - `stats.gov.cn`
   - `bea.gov`
   - other official central-bank or ministry calendars when relevant
3. Market data and flow context:
   - `stcn.com`
   - `eastmoney.com`
   - `investing.com`
4. Use secondary news only to supplement, not replace, filings or official calendars.

## Screening Workflow

### Step 1: Define the trading window

1. Anchor the analysis to the current date.
2. Convert "next week" into actual tradable dates.
3. Note exchange holidays, northbound closures, and major overnight event dates.

### Step 2: Build the candidate pool

Start from recent A-share hot stocks, usually combining:

1. high turnover leaders,
2. strong sector capital inflow,
3. liquid large- and mid-cap names with event catalysts,
4. companies with strong recent public fundamentals or industry momentum.

The candidate pool can be 20-50 names internally, but the final answer should normally mention only the top 5 unless the user asks for the full pool.

### Step 3: Score each candidate for a one-week trade

Use a simple decision framework and explain it briefly when needed:

1. `Catalyst strength`
   - event inside the next 5 trading days,
   - strong linkage between event and stock.
2. `Liquidity`
   - high turnover and easy entry/exit.
3. `Trend quality`
   - recent breakout, pullback support, or strong relative strength.
4. `Fundamental support`
   - earnings, margins, growth, pricing cycle, order visibility, or industry position.
5. `Valuation tolerance`
   - high valuation is acceptable only if catalyst and liquidity are strong.
6. `Risk asymmetry`
   - avoid names where upside is small but downside is large after a blow-off move.

## Trade-Level Rules

When providing the final 5 stocks, always include:

1. `Current reference price`
2. `Buy point`
   - preferably a pullback zone,
   - optionally a breakout trigger if the stock is still in acceleration,
   - make it clear whether the user should choose one setup or the other.
3. `Take-profit`
   - first target,
   - optional stronger second target.
4. `Stop-loss`
   - hard exit level,
   - normally below recent support or below the trigger candle logic.
5. `Position ratio`
   - total portfolio weight for that stock in this one-week plan.

Keep the total recommended allocation at `100%` unless the user asks for partial cash.

## Position Sizing Defaults

Use this default when the user does not specify risk preference:

1. strongest, most liquid setup: `20%-25%`
2. second-tier high-conviction setups: `18%-22%`
3. higher-volatility names: `15%-20%`

Adjust down when:

1. the stock is near a 52-week high after a sharp extension,
2. a major macro event is imminent,
3. the stock has an obvious overhang such as inquiry transfer or large unlock pressure.

## Risk Controls

Always state the most important short-term risk drivers, especially:

1. major macro releases inside the holding window,
2. event dates that can gap the stock up or down,
3. crowded high-valuation AI or semiconductor positioning,
4. northbound trading closures or unusual holiday effects.

If a stock is attractive only on pullback and not at the current price, say so explicitly.

## Output Contract

Unless the user asks for another format, return:

1. One short paragraph with the trading window and market condition.
2. A table with exactly these columns:
   - `股票`
   - `当前参考价`
   - `买点`
   - `止盈位`
   - `止损位`
   - `仓位比例`
   - `核心逻辑`
3. A short execution note:
   - whether to prefer low-absorption entry or breakout follow,
   - whether first target should reduce half the position.
4. A short risk note with the key dates.
5. Source links.

## Default Response Style

Be direct and actionable.
Do not bury the answer in long theory.
If the user asks for "直接给答案" or similar, shorten the explanation and keep the table first.
