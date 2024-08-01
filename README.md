//@version=4
study(title="Support Resistance EMA Indicator", overlay=true)

// Calculate EMA 50 and EMA 100
ema50 = ema(close, 50)
ema100 = ema(close, 100)

// Plot EMA 50 and EMA 100 lines
plot(ema50, color=color.blue, linewidth=2, title="EMA 50")
plot(ema100, color=color.red, linewidth=2, title="EMA 100")

// Calculate Support and Resistance levels
support = low <= ema50 ? ema50 : na
resistance = high >= ema100 ? ema100 : na

// Plot Support and Resistance levels
plot(support, color=color.green, style=plot.style_stepline, linewidth=2, title="Support")
plot(resistance, color=color.red, style=plot.style_stepline, linewidth=2, title="Resistance")

// Add labels for "B" when candlestick touches Support and "S" when touches Resistance
plotshape(series=close >= support ? close : na, location=location.belowbar, color=color.green, style=shape.labelup, text="B", title="B")
plotshape(series=close <= resistance ? close : na, location=location.abovebar, color=color.red, style=shape.labeldown, text="S", title="S")
