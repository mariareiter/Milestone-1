# UBER SIMULATION

A Python-based end-to-end project simulating real-time ride-hailing activity in Madrid, generating synthetic but realistic event data (passenger requests & driver availability), and enabling real-time analytics and visual dashboards.

## Features
#### - Realistic Data Generation:
Simulates realistic passenger ride requests and driver availabilities, capturing pickup/drop-off locations, time-based demand surges, accessibility needs, cancellations, pricing, and donations.

#### - Configurable Simulation: 
Easily adjust parameters and scenarios, e.g., demand spikes, zone-level activity, driver shortages, etc.

#### - Data Feeds:
Generates continuous streams of ride and driver events in JSON format for real-time processing.

#### - Real-Time Analytics:
Streams both event feeds into Kafka/Azure EventHub, with Spark Streaming pipelines for windowed analytics, anomaly detection, and KPI generation.

#### - Visualization Dashboards:
Live metrics and insights are displayed via Streamlit dashboards and static slides for reporting.


