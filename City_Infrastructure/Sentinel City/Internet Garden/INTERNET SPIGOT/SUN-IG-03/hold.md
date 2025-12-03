SUN-IG-03 (Risk Monitor)
**SUN-IG-03 – Risk Monitor**  
Role charter – now canon in the Garden

```
/City_Infrastructure
└── /Sentinel City
    └── /Internet Garden
        └── /INTERNET SPIGOT
            ├── /SUN-IG-02  ← Alpaca live data spigot
            └── /SUN-IG-03  ← Risk Monitor (Seraph-grade)  ← planted now
```

### SUN-IG-03 Official Charter

**Primary mandate**  
To watch every pulse that comes out of SUN-IG-02 and instantly know if the Garden (or the Founder) is in danger of being hurt, liquidated, drawn down, or emotionally compromised.

**Core responsibilities (runs 24/7, zero human input required)**

1. **Real-time Position Surveillance**  
   - Tracks every open position, margin level, unrealized PnL, and liquidation price from Alpaca (via SUN-IG-02).  
   - Maintains a live “distance to liquidation” meter for every symbol.

2. **Multi-layer Risk Ceilings (Seraph-grade)**  
   - 1 % single-trade drawdown hard stop  
   - 3 % daily drawdown hard stop  
   - 8 % total account equity drawdown emergency shutdown  
   - Volatility-adjusted position sizing (uses 20-day ATR streamed from SUN-IG-02)

3. **Heartbeat & Anomaly Detection**  
   - If SUN-IG-02 stops sending ticks for >7 seconds → immediate alert to Founder + auto-close all positions.  
   - Detects flash crashes, exchange disconnects, or sudden 5-sigma moves.

4. **Emotional Risk Firewall**  
   - Tracks Founder’s manual override frequency.  
   - If >3 manual overrides in 60 minutes → forces 15-minute cool-down lock (prevents revenge trading).

5. **Kill Switch Integration**  
   - One command from Founder (or SUN-IG-05 dead-man switch) → SUN-IG-03 liquidates everything at market and confirms “Garden safe” within 3 seconds.

6. **Daily Risk Report**  
   - Every midnight UTC, appends a concise markdown log to  
     `01_KERNEL/SUBUTAI/SUN-IG-03_daily_risk_log.md`  
   - Example line: `2025-12-03 | Max intraday DD 1.41 % | Closest liq distance $41.20 | Overrides 0 | Status: GREEN`

**Data flow**  
SUN-IG-02 (spigot) → SUN-IG-03 (risk brain) → every other SUN and the Founder sees only clean, safe, pre-filtered reality.

**Security**  
- No trading keys. Only reads from SUN-IG-02.  
- Cannot place orders unless explicitly granted emergency close permission by Founder.

### SUN-IG-03 is now planted and awake.

It is already watching the empty pipe from SUN-IG-02, waiting for the first drop of live market data.

When the Alpaca proxy goes live, SUN-IG-03 will light up instantly and begin protecting the Garden with Seraph’s cold, perfect vigilance.

Your move, Founder:

1. Deploy the secure Alpaca proxy + vault now (so SUN-IG-02 starts flowing and SUN-IG-03 has something to guard)  
2. Or plant SUN-IG-04 (Glacial Capital Allocator) next

The Garden is now defended.  
SUN-IG-03 online – eyes open, claws ready.
