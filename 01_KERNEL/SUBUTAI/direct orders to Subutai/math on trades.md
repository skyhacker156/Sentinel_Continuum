Sentinel Play-by-Play Operations Manual
 Companion Guide to the Core Math Framework
 Sentinel Laboratories
 November 15, 2025
 Purpose
 This manual provides the step-by-step operational workflow for the Sentinel Trading
 Architecture. It is written for LLMs assisting with:
 • interpreting the system math,
 • analyzing telemetry,
 • generating simulations,
 • reviewing system behavior, or
 • building code modules.
 It explains exactly what must happen, in the correct sequence, to go from raw market
 data to valid trade execution.
 Each step corresponds directly to formulas defined in the Sentinel Core Mathematical
 Framework.
 1
1 Overall System Flow
 Sentinel operates using the following strict pipeline:
 Pressure Data → TE Scan → Causal Filter → Ripeness → S3I → E(t) → Trade
 Every component must pass before a trade is allowed.
 2 Step 1: Load Telemetry Input
 The LLM begins by confirming the data sources listed in the manifest file:
 • pressure features:
 • TE fields:
 • causal validity flags:
 ϕz, ruz, midz, rspreadz
 tepos,
 teneg,
 lagpos,
 lagneg
 no signaling, observer only, past only, non intervention
 The LLM must validate:
 • rows are complete,
 • timestamps are consecutive,
 • no columns are missing.
 This corresponds to the manifest configuration.
 3 Step 2: Compute or Read Pressure States
 The LLM interprets the pressure-related variables exactly as recorded:
 • ϕz(t) : directional curvature or microstructure bias
 • ruz(t) : residual uncertainty (noise)
 • midz(t) : mid-price displacement
 • rspreadz(t) : spread compression/expansion
 These are not recalculated; the engine uses them as provided.
 LLM instructions:
 Evaluate whether pressure variables indicate strengthening, weakening, or chaotic
 conditions.
 2
4 Step 3: Transfer Entropy (TE) Scan
 The LLM now applies the TE equations from the Core Framework.
 4.1 3.1 Interpret Directional TE
 TEpos(t), TEneg(t)
 LLM must:
 • identify which direction contains meaningful TE,
 • determine whether it suggests upward or downward causal bias.
 4.2 3.2 Interpret Lag Values
 lagpos,
 lagneg
 These are read, not recalculated. LLM should check:
 • if lag falls within the expected range (1–8),
 • if strong TE aligns with a stable lag.
 4.3 3.3 Causal Validity
 LLM shall immediately discard TE values if any causal invalidity flags are active:
 {no signaling, observer only, past only, non intervention} ⇒ TEvalid(t) = 0
 If not flagged:
 At this stage:
 TEvalid(t) = max(TEpos(t),TEneg(t))
 The LLM determines if the entropy signal exists and is real. If TEvalid(t) = 0:
 stop the pipeline.
 3
5 Step 4: Ripeness Evaluation
 Ripeness measures pattern maturity:
 Ripeness(t) =
 LLM must evaluate:
 • trend alignment (1 point),
 • volume confirmation (1 point),
 • liquidity sweep event (1 point),
 • retest behavior (1 point),
 • follow-through structure (1 point).
 Execution requires:
 N
 i=1
 Ri(t)
 Ripeness(t) ≥ 3
 Crypto short optimization:
 If ripeness is below threshold:
 Ripeness(t) ≥ 4
 LLM rejects the trade idea and returns “Not ripe. Continue scanning.”
 4
6 Step 5: Compute S3I
 LLM computes or reads:
 S3I(t) = 0.25NR(t) +0.25BC(t) +0.20C(t)+0.15V(t)+0.15F(t)
 Where each sub-score comes from system logs or LLM estimation based on rolling out
come stats.
 LLM must enforce thresholds:
 S3I(t) ≥ 70 ⇒Environment acceptable
 S3I(t) < 60 ⇒Abort conditions
 LLM instruction:
 If S3I indicates noise-dominant or collapsing edge, return “Stand down.” Proceed
 only if S3I ≥ 70.
 5
7 Step 6: Execution Gate Evaluation
 The execution gate:
 LLM must check all four:
 1. S3I threshold
 2. Ripeness threshold
 3. Valid TE
 4. Pulse state not RED
 If any condition fails:
 
 
 
 
 
 
 
 
 E(t) =
 
 
 
 
 
 
 
 1 if S3I(t) ≥ 70
 ∧Ripeness(t) ≥ 3
 ∧TEvalid(t) > 0
 ∧Pulse(t) ̸ = RED
 0 otherwise
 LLM returns “Gate closed. Do not enter.”
 If all conditions pass:
 LLM returns “Gate open. Prepare execution parameters.”
 6
8 Step7:RiskandPositionSizing
 Upongateapproval,LLMcomputes:
 8.1 7.1RiskPercentage
 Risk%(t)=
 
    
    
 0.45% S3I(t)≥85
 0.35% 70≤S3I(t)<85
 0.225% 60≤S3I(t)<70
 0 S3I(t)<60
 8.2 7.2ConverttoDollars
 Risk$(t)=Risk%(t)×Equity(t)
 8.3 7.3PositionSize
 Size(t)= Risk$(t)
 |Entry−Stop|
 LLMmustensure:
 • stopdistanceiswell-defined,
 •positiondoesnotexceedriskconstraints,
 • ordersizeisappropriateforinstrumentliquidity.
 7
9 Step 8: Trade Outcome and Logging
 LLM records:
 • entry price,
 • stop price,
 • take profit,
 • risk multiple,
 • S3I at entry,
 • TE conditions,
 • ripeness score,
 • execution latency (if simulated).
 Outcome is classified using:
 R(t) = profit or loss
 risk
 10 Step 9: Update Expectancy and Equity
 Expected R-multiple:
 Expected gain per trade:
 Compounding:
 E[R] = WR·1.8−(1−WR)·1.0
 E[g] = 0.652 ×0.45% = 0.2934%
 Equity(N) = Equity(0)(1 +E[g])N
 LLM must confirm equity curve evolves according to this equation.
 8
Conclusion
 This manual defines the complete play-by-play operational flow required for an LLM to:
 • interpret Sentinel telemetry,
 • evaluate the entropy signal,
 • score ripeness,
 • compute S3I,
 • verify the execution gate,
 • size trades correctly,
 • and validate system integrity.
 No steps may be bypassed. All logic must strictly follow the gating and scoring rules
 defined here.
 9
