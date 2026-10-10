# Key Levels + Multi-Period VWAP

[English](#english) · [简体中文](#简体中文)

An independent Pine Script v6 community modification of [Key Levels SpacemanBTC IDWM](https://www.tradingview.com/script/PV6TowBV-Key-Levels-SpacemanBTC-IDWM/) by **spacemanbtc**, with the underlying base code credited to **sbtnc**. VWAP additions and maintenance are by **TrueReality** (TradingView: `truereality080`; GitHub: `RealTrueReality`).

This project is not an official SpacemanBTC release. The inherited key-level and display framework remains credited to its original authors.

## English

### Features

- Daily, weekly and monthly anchored VWAP curves.
- Optional fixed references for the final VWAP of the previous completed week and month.
- Configurable price source (HLC3 by default) and VWAP line width.
- Right-edge labels integrated with the inherited exact-price label merging.
- Inherited period opens, previous highs/lows, midpoint levels, Monday range and session ranges.
- Pine v6 migration and observed-chart-bar accumulation for developing daily/yearly highs and lows and Monday range.

### Install on TradingView

1. Open a TradingView chart and its Pine Editor.
2. Create a new indicator script.
3. Copy the entire contents of [key-levels-vwap.pine](key-levels-vwap.pine) into the editor.
4. Save the script and select **Add to chart**.
5. Open the indicator inputs and enable only the levels you need.

Start with an intraday chart. A small **Distance** value keeps labels near the latest candle; leave sufficient future space on the chart for those labels. The **Right Anchored** display places level starts in future chart space using **Anchor Distance**.

### VWAP behavior

| Reference | Reset / capture | Display |
| --- | --- | --- |
| Daily VWAP | New trading day | Intraday charts |
| Weekly VWAP | New trading week | Charts below weekly, excluding monthly |
| Monthly VWAP | New trading month | Charts below monthly |
| Previous week VWAP | Final weekly VWAP captured at the next week boundary | Fixed throughout the following week; charts below weekly |
| Previous month VWAP | Final monthly VWAP captured at the next month boundary | Fixed throughout the following month; charts below monthly |

The developing VWAP calculations use TradingView's reported chart volume and the selected price source. Current values change as market data arrives.

### Validation and limitations

The v6 script compiled and ran on TradingView using **OKX:BTCUSDT.P**, on **2-hour** and **15-minute** charts on 2026-10-10. Current daily/weekly/monthly curves and enabled previous-week/month references were visually inspected. This is a compilation and display check, not an exhaustive numerical comparison, historical replay test or a profitability backtest.

- VWAP depends on reported volume and chart-bar aggregation. Values may differ between timeframes.
- Daily/yearly and Monday ranges accumulate available chart bars; the first loaded period may be incomplete.
- Monday range is supported on intraday and daily charts. It develops during Monday and is retained for the rest of that week.
- Session inputs use the symbol's exchange timezone. Names such as London or New York do not automatically apply city-specific daylight-saving changes.
- Use standard time-based charts with usable volume data for the intended behavior.
- This indicator supplies chart references. It does not generate trade entries or place orders.

### Attribution and license

Original indicator: **spacemanbtc** — [Key Levels SpacemanBTC IDWM](https://www.tradingview.com/script/PV6TowBV-Key-Levels-SpacemanBTC-IDWM/).

The provided source acknowledges **sbtnc** for the base code; that acknowledgement is retained in the Pine file.

The source is distributed under **Mozilla Public License 2.0 (MPL-2.0)**; see [LICENSE](LICENSE). Preserve original author credits and license notices in redistributions.

## 简体中文

### 功能

在 spacemanbtc 的 Key Levels 指标基础上增加：

- 日、周、月 VWAP 曲线。
- 上一完整周、上一完整月的最终 VWAP 固定水平线。
- VWAP 价格来源（默认 HLC3）和线宽设置。
- 与原有关键价位整合的右侧标签及同价位标签合并。
- 保留原指标的周期开盘价、前期高低点、中点、周一区间与交易时段区间。
- 迁移至 Pine v6；日/年发展中高低点和周一区间从已经出现的图表 K 线累积。

### 使用

在 TradingView 的 Pine Editor 新建指标，将 [key-levels-vwap.pine](key-levels-vwap.pine) 的全部代码粘贴进去，保存后点击 **Add to chart**。建议先用日内周期，按需启用价位以减少拥挤。右侧标签需要图表预留未来空白；可减小 **Distance**。

当前 VWAP 随行情更新；上一周/上一月 VWAP 在下一周期开始时捕获完成值，并在该周期内保持固定。

### 验证与限制

2026-10-10 已在 TradingView 的 OKX BTCUSDT 永续 **2 小时、15 分钟**图表上通过编译并检查显示。尚未进行完整数值对照、历史回放或收益回测。

VWAP 受成交量数据与图表周期影响；首次加载的日、年或周一区间可能因历史不足而不完整。时段按交易品种交易所时区解释，城市名称不会自动处理夏令时。本指标提供图表参考，不自动产生交易指令。

### 致谢与许可

原指标作者：**spacemanbtc**；基础代码致谢：**sbtnc**。新增 VWAP 与维护：**TrueReality**。这是独立社区修改版，并非 SpacemanBTC 官方版本。

代码采用 [MPL 2.0](LICENSE)，保留原作者署名和许可声明。

