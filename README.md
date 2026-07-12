# SNAP HTF/LTF Indicator

SNAP HTF/LTF is a multi-timeframe TradingView Pine Script v5 indicator that maps market structure and liquidity from the weekly chart down to lower timeframes such as 5 minutes. It is designed to help traders build a top-down bias, locate where price sits within higher-timeframe dealing ranges, and identify key reaction zones and liquidity targets.

---

## Features

### Weekly Liquidity Pools
Plots the **previous week's high (PWH)** and **previous week's low (PWL)** as dashed horizontal lines.  These are major liquidity targets and reaction levels on the weekly timeframe.

### Daily Liquidity Pools
Plots the **previous day's high (PDH)** and **previous day's low (PDL)** as dashed horizontal lines for intraday liquidity awareness.

### Dealing Range (DR) with DRT Levels
Draws a shaded box over the selected reference range (Weekly or Daily) and optionally overlays three DRT (Dealing-Range-Top) grade lines:

| Level | Label | Description |
|-------|-------|-------------|
| 75 % | Premium | Upper quarter of the range — seek shorts / delivery from supply |
| 50 % | Equilibrium | Mid-range — neutral / continuation area |
| 25 % | Discount | Lower quarter of the range — seek longs / delivery from demand |

### Equal Highs & Lows (EQH / EQL)
Detects consecutive pivot highs or lows that are within a configurable percentage threshold of each other and marks them as **EQH** (equal highs) or **EQL** (equal lows).  These represent likely liquidity pools — stop clusters sitting above equal highs or below equal lows.

### Break of Structure (BOS)
Identifies when price closes beyond the most recently confirmed swing high (**bullish BOS ▲**) or swing low (**bearish BOS ▼**).  A horizontal line is drawn from the swing origin to the break bar and labelled accordingly.

### Fair Value Gaps (FVG)
Highlights three-candle imbalances:
- **Bullish FVG** — `c3.low > c1.high`; price may return to fill the gap acting as support.
- **Bearish FVG** — `c3.high < c1.low`; price may return to fill the gap acting as resistance.

Boxes extend a configurable number of bars to the right.

### Breakaway Gaps (BAG)
Marks significant price gaps on open where the opening price leaves a void above the prior candle's high (upside BAG ↑) or below the prior candle's low (downside BAG ↓).  Gap size is filtered by a minimum ATR multiple.

### 4H Breaker Blocks
Uses 4-hour structure to identify **breaker blocks** — zones that acted as order blocks but whose levels were subsequently swept by price, converting the zone from supply to demand (bullish breaker ▲) or from demand to supply (bearish breaker ▼).  Block depth is scaled to the 4H ATR for proportionality across instruments and base timeframes.

### Sunday–Monday Opening Range (SMOR)
Builds the combined high/low range from the Sunday open through the end of Monday.  Once Monday closes the range is drawn as a shaded box with a dashed mid-line.  On equity sessions where Sunday bars are absent the range defaults to Monday only.

### Deviation Zones
Projects up to **six equidistant ATR-based extension levels** above the range high and below the range low.  The source range can be:
- `SMOR` — drawn when the opening range finalises each week.
- `Daily` — redrawn at each new session open.
- `Weekly` — redrawn at each new week open.

Levels are labelled **Dev +1 … +6** (above) and **Dev −1 … −6** (below) and fade in transparency with distance so the nearest targets stand out.

---

## Settings

All features are independently togglable and fully customisable (colours, sizes, lengths) through the indicator's *Settings* panel, organised into labelled groups.

| Group | Key inputs |
|-------|-----------|
| Weekly Liquidity | Toggle, colour |
| Daily Liquidity | Toggle, colour |
| Dealing Range | Toggle, source (Weekly/Daily), DRT toggle, box/level colours |
| Equal Highs & Lows | Toggle, pivot length, match threshold % |
| Break of Structure | Toggle, swing length, bull/bear colours |
| Fair Value Gaps | Toggle, right extension (bars), bull/bear colours |
| Breakaway Gaps | Toggle, minimum gap size (ATR ×), up/down colours |
| 4H Breaker Blocks | Toggle, right extension (bars), bull/bear colours |
| Sunday–Monday Opening Range | Toggle, box colour, mid-line colour |
| Deviation Zones | Toggle, source, number of levels (1–6), ATR multiplier, colour |

---

## Usage

1. Open TradingView and create a new Pine Script indicator.
2. Paste the contents of `SNAP_HTF_LTF.pine` into the Pine Editor.
3. Click **Add to chart**.
4. Adjust settings in the indicator panel to suit your instrument and session.

> **Recommended timeframes:** 5 min – 1 H for intraday setups; 4 H – Daily for swing setups.  Weekly and daily levels are always drawn from their respective higher-timeframe data regardless of the chart timeframe.
