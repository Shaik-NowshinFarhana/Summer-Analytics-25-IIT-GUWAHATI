ASSIGNMENT-1   JUPYTER NOTEBOOK :- https://jupyter.org/try-jupyter/lab/index.html
ASSIGNMENT URL:-https://jupyter.org/try-jupyter/lab/index.html?path=SA2025_W1.ipynb
![image](https://github.com/user-attachments/assets/e42ae39a-47c3-44e8-8ebc-e099e847f9af)



# Dynamic Pricing for Urban Parking Lots

## 🧭 Overview

This project implements a *real-time pricing engine* for urban parking lots using streaming data. The system adjusts prices dynamically based on real-time demand, competition from nearby lots, and environmental factors. Built as part of the *Summer Analytics 2025 Capstone*, it uses Python, Pandas, Pathway, and Bokeh to create intelligent and interpretable pricing models.

## 🛠 Tech Stack

| Layer             | Technology      |
| ----------------- | --------------- |
| Programming       | Python          |
| Data Manipulation | Pandas, NumPy   |
| Real-Time Engine  | Pathway         |
| Visualization     | Bokeh           |
| Documentation     | Markdown, LaTeX |

## 🧱 Project Models

* *Model 1*: Linear pricing based on occupancy
* *Model 2*: Demand-based pricing using multiple real-time features
* *Model 3*: Competitive pricing that includes geo-aware pricing logic with rerouting

## 📐 Architecture Diagram

mermaid
graph TD                                                                        



    A[CSV Input Stream] -->|streaming| B[Pathway Schema]
    B --> C[Model 1 - Linear Pricing]
    B --> D[Model 2 - Demand-Based Pricing]
    B --> E[Model 3 - Competitive Pricing]
    E --> F{Haversine Join for Nearby Lots}
    F --> G[Price Adjuster Logic]
    G --> H[Final Price + Reroute Output]
    H --> I[Bokeh Visual Dashboard]


## 🔁 Architecture & Workflow

### 🔹 Input

* Historical data is streamed using Pathway.replay_csv().
* Features include: Occupancy, Capacity, QueueLength, TrafficConditionNearby, IsSpecialDay, VehicleType, and geo-coordinates.

### 🔹 Model Pipeline

* *Pathway Schema* ingests data and applies transformations.
* *Model 1* applies simple linear rules using occupancy rate.
* *Model 2* computes normalized demand and outputs smoothed pricing.
* *Model 3* performs a self-join (within 1 km) to identify local competitors and apply reroute-aware pricing strategies.

### 🔹 Price Adjustment Logic

* Nearby prices and occupancies are averaged.
* UDF (adjust_price) adjusts the price if the lot is full or empty relative to the neighborhood.
* Prices are clipped to the range \[\$5, \$20].

### 🔹 Output & Visualization

* Final outputs include FinalPrice and SuggestReroute.
* Bokeh dashboard visualizes pricing trends over time with interactive hover tools and reroute indicators.

## 📦 Deliverables

* Python + Pathway real-time engine script
* Bokeh-based visualizations
* Final LaTeX report
* This README.md

## 🧩 How to Run

1. Clone the repo
2. Install dependencies:

bash
pip install pandas numpy pathway bokeh


3. Run the main notebook or Python script
4. Use Bokeh server (optional) for dashboard

## 📄 Resources

* [Pathway: From Jupyter to Deploy](https://pathway.com/developers/user-guide/deployment/from-jupyter-to-deploy/)
* [Pathway: First Real-Time App](https://pathway.com/developers/user-guide/introduction/first_realtime_app_with_pathway/)
* [Summer Analytics 2025](https://www.caciitg.com/sa/course25/)
