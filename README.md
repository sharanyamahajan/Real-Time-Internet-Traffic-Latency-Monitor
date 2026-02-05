# Real-Time Internet Traffic & Latency Monitor

## Overview
A production-grade, real-time dashboard that visualizes how internet traffic flows across the globe, including latency, packet loss, jitter, and CDN routing paths. The platform is designed to model large-scale network behavior and can start with synthetic data (v1) before integrating real-world probes (v2).

## Core Capabilities
- **Global latency heatmap** with color-coded regions and animated traffic pulses.
- **Real-time packet loss & jitter charts** with automatic spike detection and tooltips.
- **CDN routing visualization** showing origin → edge → user paths with map animations.
- **WebSocket-based live updates** to avoid polling overhead and keep the UI responsive.

## System Architecture (High Level)
```
┌────────────────────────────────────────────────────────┐
│                    CLIENT (Web App)                    │
│                                                        │
│  World Map + Charts + Routing Animation                │
│  React + D3 / Mapbox                                   │
│                                                        │
│  WebSocket Client (live updates)                       │
└───────────────┬────────────────────────────────────────┘
                │ WebSocket / REST
┌───────────────▼────────────────────────────────────────┐
│              REAL-TIME DATA ENGINE (BFF)               │
│                                                        │
│  Latency Simulator / Collector                         │
│  Packet Loss Generator                                 │
│  CDN Path Resolver                                     │
│                                                        │
│  Node.js + TypeScript                                  │
└───────────────┬────────────────────────────────────────┘
                │
┌───────────────▼────────────────────────────────────────┐
│           DATA SOURCES (v1 → v2)                       │
│                                                        │
│  v1: Synthetic traffic model                           │
│  v2: Public probes / RIPE Atlas / Cloud APIs           │
│                                                        │
└────────────────────────────────────────────────────────┘
```

## Simulation Logic (v1)
Synthetic data starts with realistic network models:

- `latency = baseDistanceLatency + congestionFactor + randomJitter`
- `packetLoss = congestion > threshold ? random(1–5%) : <1%`

This enables deterministic scenarios, clear interview explanations, and reliable demo data.

## Interview-Ready Talking Points
- “We used WebSockets to avoid polling overhead.”
- “Latency models are distance + congestion based.”
- “Visualization focuses on p95, not just averages.”
- “System is extensible to real probes later.”
- “Map rendering is optimized to avoid reflows.”

## Resume Line
**Real-Time Internet Traffic & Latency Monitor** — Built a real-time global network visualization platform using React, D3, and WebSockets to model latency, packet loss, and CDN routing paths across regions. Designed synthetic traffic models and animated world-map visualizations to simulate large-scale internet infrastructure behavior.

## Roadmap
- [ ] Next.js + TypeScript frontend scaffold
- [ ] WebSocket data engine with synthetic traffic generator
- [ ] Map visualization with latency heatmap and routing animations
- [ ] Packet loss & jitter time-series charts
- [ ] Alerting thresholds and region comparisons
- [ ] Optional dark mode + latency replay
