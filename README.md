# Green-Pulse

> **AI-coordinated emergency traffic control for faster ambulance movement through Chennai.**

Green-Pulse is a smart emergency corridor system that dynamically coordinates traffic signals to help ambulances reach hospitals faster while minimizing disruption to normal traffic.

---

## Overview

Traditional green corridors often clear an entire route for an emergency vehicle, which can create unnecessary delays for thousands of other road users.

**Green-Pulse uses a rolling, intelligent corridor instead.**

The system continuously evaluates:

- Emergency severity
- Current traffic conditions
- Estimated travel time
- Multiple emergency vehicles
- Recent disruption caused to roads
- Junction-level conflicts

This allows the system to prioritize emergency vehicles while keeping the overall traffic impact as low as possible.

---

## Key Features

### Real-Time Route Optimization

Uses **time-weighted Dijkstra / A\*** routing to select the fastest route based on current traffic conditions rather than simply choosing the shortest physical route.

### Rolling Green Corridor

Instead of blocking the entire route for the complete journey, signal priority is activated progressively around the emergency vehicle.

### Multi-Emergency Arbitration

When multiple emergency vehicles require the same junction, Green-Pulse resolves the conflict using a priority-based decision system.

Priority considers:

**Severity + Remaining ETA + Wait-Time Penalty − Fairness Debt**

Ties are resolved using ETA and timestamp, making decisions deterministic and reproducible.

### Fairness / Debt Score

Roads accumulate a **debt score** when they are repeatedly held for emergency corridors.

The score gradually decays when a road is not used, encouraging the system to distribute traffic disruption without completely preventing the fastest route from being selected.

### Continuous Re-Evaluation

Routes and signal priorities are continuously recalculated as traffic and emergency conditions change.

### Data Validation

Incoming dispatch requests, GPS updates, and hospital registrations pass through a strict validation layer before reaching the routing and priority engines.

---

## System Workflow

```text
Emergency Dispatch
        ↓
Dispatch Ingestion
        ↓
Data Validation
        ↓
Route Computation
        ↓
Priority + Conflict Check
        ↓
Rolling Corridor Activation
        ↓
Continuous Re-evaluation
        ↓
Signal Handback
        ↓
Decision Logging# Green-pulse
AI-coordinated traffic signal control that gets ambulances through Chennai's junctions faster, without holding the rest of the city hostage to do it.
