# SolarHMI_ModeBus_JS
This project is being developed for solar power plant data  in HMI.
# 🌞 Solar Monitor System

**Solar Monitor** is an open‑source solar monitoring platform that simulates inverter data (voltage, power, current, temperature) and visualizes it live through a **React Dashboard**.  
The system collects operational data via a mock Node.js collector, stores it in **TimescaleDB**, and serves it through an **Express API**.

---

## ⚙️ Project Structure
solar-monitor/

├── collector/ # Mock data generator (simulated inverter)

├── backend/ # Express API (data access layer)

├── frontend/ # React + D3 dashboard (visual layer)

├── docker/ # Optional Docker setup files

└── README.md


🧩 System Layers (A–B–C–D Model)
A: Field Layer → Physical environment (solar panels)
B: Equipment Layer → Inverter and sensors
C: Protocol Layer → Data communication (Collector ↔ Backend)
D: Software Layer → Dashboard and visualization
🌟 Features
Mock generation of inverter data (voltage, power, current, temperature)
Automatic data storage every 5 seconds in TimescaleDB
REST API access with Express.js
Real‑time charting using React + D3.js
Ready for upgrade to WebSocket live updates
🚀 Getting Started (Development Mode)
Prerequisites
Node.js ≥ 18
PostgreSQL / TimescaleDB
npm or yarn
Installation

content_copy
bash
cd collector && npm install
cd ../backend && npm install
cd ../frontend && npm install
Environment Setup
Create a .env file in each folder:


content_copy
env
DB_HOST=localhost
DB_USER=admin
DB_PASSWORD=1234
DB_NAME=solar_monitor
Run the mock collector

content_copy
bash
node collector.js
Run the backend API

content_copy
bash
node server.js
Run the frontend dashboard

content_copy
bash
npm start
🧠 API Endpoints
Endpoint	Description	Example
/api/data/latest	Returns latest recorded data	{ voltage: 580, power: 3000, current: 5.2, temperature: 46 }
/api/data/history	Returns historic averaged data (5‑min intervals)	[ { time: ..., voltage: ..., power: ... } ]
🧱 Technologies Used
Node.js (Collector & Server)
Express.js
PostgreSQL / TimescaleDB
React.js + D3.js
Docker Compose (optional)
🧰 Collector Example

content_copy
javascript
// collector.js
import db from './db.js';
import { randomBetween } from './utils.js';

setInterval(async () => {
  const data = {
voltage: randomBetween(520, 620),
power: randomBetween(2500, 4800),
current: randomBetween(4.5, 8.0),
temperature: randomBetween(35, 55),
  };
  await db.insert(data);
}, 5000);
📈 Roadmap
Enable WebSocket real‑time live updates
Add Alert system for threshold warnings
Connect to physical inverter via Modbus TCP
🪪 License
MIT License © 2025 [Your Name]

💡 Contributing
Contributions are welcome!

To suggest new features or report bugs, please open a GitHub issue or submit a pull request.

🧭 References
TimescaleDB Documentation
D3.js Official Sitennection variables:

