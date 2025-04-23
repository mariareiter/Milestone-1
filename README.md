# UBER SIMULATION

A Python-based end-to-end project simulating real-time ride-hailing activity in Madrid, generating synthetic but realistic event data (passenger requests & driver availability), and enabling real-time analytics and visual dashboards.

---

## Features

- **Synthetic Data Generation:**  
  Realistic simulation of passenger ride requests and driver availabilities, including zone-level locations, demand surges, cancellations, pricing, accessibility needs, and more.
- **Real-Time Processing:**  
  Streams two event feeds (requests & driver status) into Kafka/EventHub, with Spark Streaming pipelines for real-time analytics, KPIs, and anomaly detection.
- **Analytics Dashboards:**  
  Key platform metrics and business insights visualized in real time (Streamlit app and static slides).
- **Configurable & Extensible:**  
  Easy to adjust scenario parameters, add new analytics, or plug into your own Azure/Kafka/Spark infra.

---

## Data Feeds & Format

### 1. Passenger Request Events

| Field                  | Description                                   |
|------------------------|-----------------------------------------------|
| request_id             | Unique ride request ID                        |
| passenger_id, name     | Passenger identifier, name                    |
| pickup_zone, dropoff_zone | Pickup and dropoff area/zone              |
| pickup_lat/lon, dropoff_lat/lon | GPS coordinates                      |
| request_time           | Timestamp of request creation                 |
| status                 | Current ride status ("requested", "completed", etc.) |
| cancellation_time      | Timestamp of cancellation (if any)            |
| ride_duration          | Simulated ride length (min)                   |
| vehicle_type           | Category requested ("standard", "premium", etc.) |
| estimated_eta          | Estimated driver ETA                          |
| demand_level           | "High", "Medium", "Low"                       |
| price                  | Simulated trip price (€)                      |
| driver_rating, passenger_rating | Ratings (1-5)                      |
| favorite_location      | e.g. "Home", "Work", "Airport"                |
| is_wheelchair_accessible | Accessibility flag                          |
| scheduled_time         | Scheduled ride time (if any)                  |
| donation_amount        | Optional tip/donation                         |
| vehicle_license_plate  | Car identifier                                |

### 2. Driver Availability Events

| Field                   | Description                                  |
|-------------------------|----------------------------------------------|
| driver_id, driver_name  | Driver identifier, name                      |
| status                  | "available", "unavailable"                   |
| zone                    | Current service zone                         |
| update_time             | Timestamp of status update                   |
| driver_rating           | Average driver rating                        |
| is_wheelchair_accessible| Accessibility flag                           |
| vehicle_license_plate   | Car identifier                               |

#### Example Data Files

- `passenger_requests.json` – Passenger request events
- `driver_availability.json` – Driver availability snapshots

---

## Project Structure

```
project-root/
│
├── data/
│   ├── passenger_requests.json
│   ├── driver_availability.json
│
├── notebooks/
│   ├── Milestone 1.ipynb
│   ├── implementation.ipynb
│   └── spark_streaming_analysis.ipynb
│
├── app/
│   └── streamlit_dashboard.py
│
├── README.md
└── requirements.txt
```

---

## Simulation & Streaming Pipeline

1. **Data Generator**:  
   Produces continuous streams of passenger/driver events for Madrid, with realistic demand, zone distribution, cancellations, surge, and accessibility needs.
2. **Event Streaming**:  
   Feeds are pushed to Kafka or Azure EventHub topics (`passenger_requests`, `drivers_availability`).
3. **Spark Streaming**:  
   Real-time ingestion, windowing, enrichment, and analytics computation (see notebooks for implementation).
4. **Storage**:  
   Raw and aggregated results stored in Azure Blob (Parquet) or local storage.
5. **Dashboards**:  
   Live KPIs, graphs, and anomaly alerts visualized in Streamlit (and exported as slides for presentations).

---

## Key Analytics & Use Cases

- **Zone-Level Demand vs. Supply**  
  - Tracks per-zone event counts, identifies shortages, visualizes hot spots (time series + city heatmap).
- **Cancellation Monitoring**  
  - Computes real-time cancellation rates, raises alerts on spikes (line/bar chart with alert highlights).
- **ETA Accuracy & Driver Response**  
  - Compares estimated vs. actual wait times by vehicle type (scatter, boxplot).
- **Accessibility Demand vs. Supply**  
  - Monitors accessible ride fulfillment by zone (stacked bar chart).
- **Anomaly & Surge Detection**  
  - Detects outlier surges, pricing anomalies, and demand-supply imbalances.
- **Passenger Satisfaction & Donation Analytics**  
  - Correlates ratings and donation patterns by time, zone, and vehicle type.

---

## Quick Start

1. **Clone the Repository:**
    ```sh
    git clone https://github.com/your-username/your-ride-hailing-sim.git
    cd your-ride-hailing-sim
    ```
2. **(Optional) Create Virtual Environment:**
    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```
3. **Install Dependencies:**
    ```sh
    pip install -r requirements.txt
    ```
4. **Run Data Generator / Simulation:**  
   See `notebooks/Milestone 1.ipynb` for data generation details.

5. **Launch Dashboards:**  
   ```sh
   streamlit run app/streamlit_dashboard.py
   ```

6. **Explore Analytics:**  
   - Real-time graphs, heatmaps, and KPIs.
   - Jupyter notebooks for deeper analytics.


---


