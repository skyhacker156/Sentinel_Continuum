Perfect. This is **Tier-2 Architecture** all day long — it defines how S³ outputs are *rendered*, not how they’re *computed*.

👉 **Where to put it in the repo**

Create this file:

`/S3/02_Tier2_Architecture/S3_T2_Pressure_Barometer_Implementation_Guide.md`

Then paste the badge-ified version below into it.

---

````markdown
S3_T2_Pressure_Barometer_Implementation_Guide.md  
Badge: BADGE3_STEWARD  
Classification: Tier-2 | Architecture Layer | Frontend Spec  
Containment: Above Doctrine, Below Execution  
Authority: Founder-exclusive modification  
Status: Prototype Architecture – Doctrine-Safe, Engine-Agnostic  

---

# SENTINEL PRESSURE BAROMETER
## React/TypeScript Implementation Guide

**Status:** Prototype Ready for Development  
**Current Phase:** Core Components Complete, Mock Data Integration  

> Tier-2 note: This document describes **only** how already-computed S³ fields are displayed in a React UI.  
> It never defines how Φ, η, CAI, V(t), or Shadow Momentum are calculated. The engine remains sealed.

---

## ARCHITECTURE OVERVIEW

### File Structure

```text
sentinel-barometer/
├── src/
│   ├── components/
│   │   ├── PressureGauge.tsx          # Φ_norm circular gauge
│   │   ├── VelocitySpeedometer.tsx    # V(t) semicircle gauge
│   │   ├── ClarityIndicator.tsx       # η, CAI, clarity state
│   │   ├── BarometerPanel.tsx         # Integrated single-asset barometer
│   │   └── MultiAssetGrid.tsx         # (TODO) 6-12 asset grid
│   ├── hooks/
│   │   ├── useBarometerStore.ts       # Zustand state management
│   │   └── useDataStream.ts           # (TODO) Real data integration
│   ├── types/
│   │   └── index.ts                   # TypeScript interfaces
│   ├── utils/
│   │   ├── mockData.ts                # Mock data generation
│   │   └── dataTransforms.ts          # (TODO) Data normalization
│   ├── styles/
│   │   └── globals.css                # (TODO) Global styles
│   └── App.tsx                        # Main app component
├── public/
│   └── index.html
├── package.json
├── tsconfig.json
└── vite.config.ts
````

---

## COMPONENT HIERARCHY

```text
App
├── Control Panel (Start/Stop, Speed)
├── BarometerPanel (BTC/USD)
│   ├── PressureGauge (Φ_norm)
│   ├── VelocitySpeedometer (V(t))
│   ├── ClarityIndicator (η, CAI, clarity)
│   ├── Shadow Momentum display
│   └── Entry/Exit buttons
└── Action Log
```

---

## DATA FLOW

### 1. Backend → Frontend

The S³ backend returns this JSON every 5 seconds (or on-demand).
Values are treated as **opaque fields** at this layer:

```json
{
  "phi_norm": 0.45,
  "eta": 0.52,
  "cai": 0.87,
  "v": 0.12,
  "sm": 0.38,
  "clarity_state": true,
  "entry_valid": true,
  "exit_signal": false,
  "timestamp": 1700761200000,
  "open": 45010.50,
  "high": 45234.75,
  "low": 44891.25,
  "close": 45123.40,
  "volume": 1234567
}
```

### 2. Frontend Processing

```text
Backend JSON
    ↓
useBarometerStore.updatePressure()
    ↓
Store calculates:
  - clarity_duration_bars
  - pressure_trend
  - exit_probability (UI-facing, not trade engine logic)
    ↓
Components read from store
    ↓
Render updated UI
```

### 3. User Interaction

```text
User clicks ENTRY/EXIT button
    ↓
Handler function (onEntry, onExit)
    ↓
Log action with timestamp
    ↓
(Optionally) call external trading system – outside this spec
```

---

## IMPLEMENTATION PHASES

### Phase 1: Core Components

**Status:** ✅ COMPLETE

* [x] PressureGauge.tsx
* [x] VelocitySpeedometer.tsx
* [x] ClarityIndicator.tsx
* [x] BarometerPanel.tsx
* [x] State management (Zustand)
* [x] Types and interfaces

### Phase 2: Data Integration

**Status:** 🔄 IN PROGRESS

* [ ] Replace mock data with real backend API
* [ ] Create `useDataStream` hook for WebSocket connection
* [ ] Add error handling and reconnection logic
* [ ] Add data normalization and validation
* [ ] Historical data retrieval for backtesting

```ts
// hooks/useDataStream.ts
export const useDataStream = (asset_symbol: string, backend_url: string) => {
  const updatePressure = useBarometerStore((state) => state.updatePressure);

  useEffect(() => {
    const ws = new WebSocket(`${backend_url}/pressure/${asset_symbol}`);
    
    ws.onmessage = (event) => {
      const data = JSON.parse(event.data) as PressureState;
      updatePressure(data);
    };

    return () => ws.close();
  }, [asset_symbol, backend_url, updatePressure]);
};
```

### Phase 3: Multi-Asset Dashboard

**Status:** ⏳ PENDING

* [ ] MultiAssetGrid component (6–12 panels)
* [ ] Panel resizing by coherence strength
* [ ] Asset sorting by V(t) velocity
* [ ] Correlation heatmap
* [ ] Asset switching UI

### Phase 4: Production Polish

**Status:** ⏳ PENDING

* [ ] Responsive design (mobile/tablet/desktop)
* [ ] Theme system (dark/light mode)
* [ ] Performance optimization
* [ ] Error boundaries and error handling
* [ ] Unit tests (Jest + React Testing Library)
* [ ] E2E tests (Cypress)
* [ ] Documentation

---

## HOW TO RUN LOCALLY

### Prerequisites

* Node.js 18+
* npm or yarn
* Git

### Setup

```bash
# Clone repository
git clone https://github.com/sentinel-labs/sentinel-barometer.git
cd sentinel-barometer

# Install dependencies
npm install

# Start development server
npm run dev

# Open in browser
# http://localhost:5173
```

### Start Streaming

1. Click **START STREAM**
2. Choose update frequency (5 seconds recommended)
3. Watch the barometer update in real time
4. Click **ENTRY** when `entry_valid = true`
5. Click **EXIT** when `exit_signal = true`
6. View actions in the log

---

## INTEGRATING REAL DATA

### Step 1: API client

```ts
// utils/api.ts
export const getPressureState = async (symbol: string): Promise<PressureState> => {
  const response = await fetch(`/api/pressure/${symbol}`);
  return response.json();
};

export const subscribeToStream = (
  symbol: string,
  callback: (state: PressureState) => void
) => {
  const ws = new WebSocket(`ws://localhost:8000/stream/${symbol}`);
  ws.onmessage = (event) => callback(JSON.parse(event.data));
  return () => ws.close();
};
```

### Step 2: Replace mock data hook

```ts
// In App.tsx
const handleEntry = useCallback(async () => {
  if (current) {
    // Call your trading API (external to S³ engine)
    await executeEntry({
      symbol: 'BTC/USD',
      price: current.close,
      quantity: 1,
    });
  }
}, [current]);
```

### Step 3: Add real assets

```ts
// Example multi-asset wiring
const [assets] = useState(['BTC/USD', 'ETH/USD', 'SOL/USD']);
const multiAsset = useMultiAssetStore();

useEffect(() => {
  assets.forEach((asset) => {
    multiAsset.addAsset(asset);
    subscribeToStream(asset, (state) => {
      multiAsset.updateAsset(asset, state);
    });
  });
}, [assets]);
```

---

## TESTING

### Unit Tests

```bash
npm run test
```

Example:

```ts
// components/__tests__/PressureGauge.test.tsx
import { render, screen } from '@testing-library/react';
import { PressureGauge } from '../PressureGauge';

describe('PressureGauge', () => {
  it('renders green when pressure is high', () => {
    render(<PressureGauge phi_norm={2.0} />);
    const gauge = screen.getByRole('img');
    expect(gauge).toHaveStyle('color: rgb(68, 255, 68)');
  });

  it('renders red when pressure is low', () => {
    render(<PressureGauge phi_norm={-2.0} />);
    const gauge = screen.getByRole('img');
    expect(gauge).toHaveStyle('color: rgb(255, 68, 68)');
  });
});
```

### Manual Testing Checklist

* [ ] Pressure gauge updates correctly with `phi_norm`
* [ ] Velocity speedometer needle moves
* [ ] Clarity indicator shows correct states
* [ ] Entry button enables when `entry_valid = true`
* [ ] Exit button enables when `exit_signal = true`
* [ ] Ghost bar reflects shadow momentum direction
* [ ] Action log records all trades
* [ ] Responsive on mobile, tablet, desktop
* [ ] No console errors

---

## PERFORMANCE CONSIDERATIONS

### Current

* Single asset: ~60fps smooth rendering
* Mock data stream: 5–20 updates/second

### Scaling to Multi-Asset

* 6 assets: ~50fps (acceptable)
* 12 assets: ~30fps (acceptable, may need optimization)
* 50+ assets: requires virtualization (render only visible panels)

### Optimization Strategies

1. Use `React.memo` for components
2. Virtualize grid for 50+ assets (`react-window`)
3. Debounce store updates if needed
4. Prefer CSS animations where possible

---

## SECURITY & CLASSIFICATION

**Classification:** INTERNAL — Founder & Systems Leads Only

✅ Safe to expose at Tier-2:

* Component rendering logic
* UI/UX design
* Data structures and wiring

❌ Never expose from this file:

* How Φ, η, CAI, V(t), or Shadow Momentum are calculated
* Threshold values
* Signal definitions
* Any implementation details of the S³ engine

The backend remains sealed.
The barometer only **renders** what the backend sends.

---

## SUPPORT & TROUBLESHOOTING

**Q: Data not updating?**
A: Confirm stream running, check WebSocket URL, inspect browser console.

**Q: Colors look wrong?**
A: Verify spec values in component files match barometer visual spec (v1.1).

**Q: Exit button not appearing?**
A: Exit appears when `exit_signal = true` (and any additional UI rules you define).

**Q: Performance is slow?**
A: Check number of assets; for 50+ enable grid virtualization.

---

## NEXT STEPS

1. Integrate real data connection (replace mock stream)
2. Add multi-asset grid (6 assets minimum)
3. Deploy to staging environment
4. Beta test with 10–20 internal users
5. Gather feedback and iterate
6. Approve for production launch under Sentinel Labs change control

---

```
