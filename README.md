# 🐟 Aquaculture Water Quality Monitoring

IoT system to monitor the water quality of fish farms in real time. Sensors measure the water, an embedded system sends the data, and a web dashboard shows the measurements, their history and their location.

Project carried out during my internship at **Exypnotech** (Tunisia, 2024).

## System architecture

```
Sensors (pH, temperature, turbidity, dissolved oxygen)
        │
     STM32 board  ── data acquisition
        │  LoRa (SX1278)
   Raspberry Pi   ── gateway
        │  REST API
 Node.js / Express backend + MongoDB
        │
   React web dashboard
```

## Measured parameters

- pH
- Temperature
- Turbidity
- Dissolved oxygen (DO)

## Dashboard features

- **Live monitoring:** gauges and charts for each parameter
- **History:** table and bar charts of past measurements, by month
- **Map:** map view of the monitoring site (Leaflet), currently with a demo marker
- **Login:** user accounts with JWT authentication

## Tech stack

| Part | Technologies |
|---|---|
| Embedded | STM32, LoRa SX1278, Raspberry Pi, UART, I²C |
| Backend | Node.js, Express, MongoDB (Mongoose), JWT, bcrypt |
| Front end | React, React Router, Axios, Recharts, React Google Charts, React Leaflet |

## Project structure

```
├── front-end/            # React web dashboard
│   └── src/
│       ├── api/          # API client (Axios)
│       └── components/   # Charts, history, map, login
└── mycontacts-backend/   # Express REST API
    ├── routes/           # Sensors, water systems, users, companies
    ├── controllers/
    ├── models/           # MongoDB models
    └── middlewatre/      # Error handling and JWT validation
```

## Getting started

### Backend

```bash
cd mycontacts-backend
npm install
```

Create a `.env` file:

```
CONNECTION_STRING=mongodb+srv://<user>:<password>@<cluster>/<database>
ACCESS_TOKEN_SECRET=<your-secret>
PORT=5001
```

Then run `npm run dev`.

### Front end

```bash
cd front-end
npm install
npm start
```

The dashboard opens at http://localhost:3000 and calls the API at `http://localhost:5001/api`.

## Author

Skandar Makari · [GitHub](https://github.com/MakariSkander)
