# 🅿️ ParkLink

> **A Real-Time Parking Space Sharing and Allocation Platform Connecting Vehicle Owners and Space Providers**

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.104+-009688?style=flat-square&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![React](https://img.shields.io/badge/React-18+-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev)
[![Firebase](https://img.shields.io/badge/Firebase-Latest-FFCA28?style=flat-square&logo=firebase&logoColor=black)](https://firebase.google.com)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.3+-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

---

## 📌 Overview

ParkLink is a full-stack, real-time parking space sharing platform that bridges the gap between vehicle owners looking for parking and space providers with available lots. Using live WebSocket updates, machine learning-based demand forecasting, and a seamless React-based UI, ParkLink makes urban parking smarter, faster, and more efficient.

---

## ✨ Features

- 🔴 **Real-time slot availability** — Live updates via WebSocket when slots are booked or freed
- 📍 **Geo-based search** — Find nearby parking spaces using the browser's Geolocation API
- 🤖 **ML-powered predictions** — Demand forecasting, dynamic pricing, and occupancy prediction
- 👤 **Dual user roles** — Separate flows for vehicle owners (drivers) and space providers
- 🔐 **Secure authentication** — Email, phone OTP, and Google OAuth via Firebase Auth
- 💸 **Dynamic pricing engine** — Surge pricing during peak hours using ML models
- 📊 **Analytics dashboard** — Parking heatmaps and usage statistics
- 🖼️ **Space media uploads** — Photo and document management via Firebase Storage

---

## 🛠️ Tech Stack

```
Python | FastAPI | React JS | HTML | CSS | JavaScript | Firebase | Machine Learning | Scikit-learn
```

| Layer | Technology | Purpose |
|---|---|---|
| **Frontend** | React JS | Component-based SPA, real-time map & booking UI |
| **Frontend** | HTML5 | Semantic markup, Geolocation API integration |
| **Frontend** | CSS3 | Responsive grid layout, parking slot UI |
| **Frontend** | JavaScript (ES2024) | Real-time interactions, maps, booking logic |
| **Backend** | Python 3.11+ | Core language for all services |
| **Backend** | FastAPI | REST APIs + WebSocket for live slot streaming |
| **Database** | Firebase Firestore | Real-time NoSQL — live slot availability sync |
| **Auth** | Firebase Auth | OAuth2, email/phone login for drivers & owners |
| **Storage** | Firebase Storage | Parking space images & permit documents |
| **ML** | Machine Learning | Demand forecasting & dynamic pricing engine |
| **ML** | Scikit-learn | Slot prediction, occupancy & user clustering |
| **Hosting** | Firebase Hosting | CDN deployment for React frontend |

---

## 📁 Project Structure

```
parklink/
├── backend/
│   ├── main.py                  # FastAPI app entry point
│   ├── routes/
│   │   ├── auth.py              # Authentication routes
│   │   ├── slots.py             # Parking slot CRUD & WebSocket
│   │   ├── bookings.py          # Booking management
│   │   └── users.py             # User profile routes
│   ├── models/
│   │   ├── slot.py              # Slot data models
│   │   ├── booking.py           # Booking data models
│   │   └── user.py              # User data models
│   ├── ml/
│   │   ├── demand_forecast.py   # Scikit-learn demand model
│   │   ├── dynamic_pricing.py   # Pricing engine
│   │   └── occupancy_predict.py # Slot occupancy predictor
│   ├── firebase/
│   │   ├── config.py            # Firebase admin SDK setup
│   │   └── firestore.py         # Firestore helpers
│   └── requirements.txt
│
├── frontend/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/
│   │   │   ├── Map/             # Real-time parking map
│   │   │   ├── SlotCard/        # Individual slot component
│   │   │   ├── BookingModal/    # Booking flow UI
│   │   │   └── Dashboard/       # Analytics dashboard
│   │   ├── pages/
│   │   │   ├── Home.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── ProviderDashboard.jsx
│   │   │   └── DriverDashboard.jsx
│   │   ├── hooks/
│   │   │   ├── useWebSocket.js  # Live slot updates hook
│   │   │   └── useGeolocation.js
│   │   ├── firebase/
│   │   │   └── config.js        # Firebase client config
│   │   ├── App.jsx
│   │   └── index.js
│   └── package.json
│
├── ml_models/
│   ├── train_demand.py          # Training scripts
│   ├── train_pricing.py
│   └── saved_models/            # Serialized .pkl models
│
├── .env.example
├── .gitignore
├── docker-compose.yml
└── README.md
```

---

## ⚙️ Installation & Setup

### Prerequisites

- Python 3.11+
- Node.js 18+
- Firebase project (Firestore, Auth, Storage, Hosting enabled)

---

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/parklink.git
cd parklink
```

---

### 2. Backend Setup (FastAPI)

```bash
cd backend
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Create a `.env` file in `/backend`:

```env
FIREBASE_CREDENTIALS_PATH=./firebase/serviceAccountKey.json
SECRET_KEY=your_secret_key_here
ALLOWED_ORIGINS=http://localhost:3000
```

Place your Firebase service account JSON at `backend/firebase/serviceAccountKey.json`.

Start the backend server:

```bash
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

API docs available at: `http://localhost:8000/docs`

---

### 3. Frontend Setup (React JS)

```bash
cd frontend
npm install
```

Create a `.env` file in `/frontend`:

```env
REACT_APP_FIREBASE_API_KEY=your_api_key
REACT_APP_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
REACT_APP_FIREBASE_PROJECT_ID=your_project_id
REACT_APP_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
REACT_APP_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
REACT_APP_FIREBASE_APP_ID=your_app_id
REACT_APP_BACKEND_URL=http://localhost:8000
```

Start the development server:

```bash
npm start
```

Frontend runs at: `http://localhost:3000`

---

### 4. Machine Learning Models

```bash
cd ml_models
python train_demand.py       # Train demand forecasting model
python train_pricing.py      # Train dynamic pricing model
```

Trained models are saved to `ml_models/saved_models/` as `.pkl` files and loaded by the FastAPI backend automatically.

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/slots/nearby` | Get parking slots near coordinates |
| `POST` | `/slots/` | Create a new parking slot (Provider) |
| `PATCH` | `/slots/{id}` | Update slot availability |
| `POST` | `/bookings/` | Create a booking |
| `GET` | `/bookings/{user_id}` | Get user booking history |
| `GET` | `/ml/predict/demand` | Get demand forecast for an area |
| `GET` | `/ml/price/dynamic` | Get dynamic price for a slot |
| `WS` | `/ws/slots` | WebSocket — live slot availability stream |

---

## 🤖 Machine Learning Models

### Demand Forecasting
- **Algorithm:** Random Forest Regressor (Scikit-learn)
- **Input features:** Time of day, day of week, location zone, weather, events
- **Output:** Expected demand score (0–100) for next 30/60 minutes

### Dynamic Pricing Engine
- **Algorithm:** Gradient Boosting Regressor
- **Input features:** Demand score, distance to city centre, historical bookings, slot rating
- **Output:** Recommended price per hour

### Occupancy Prediction
- **Algorithm:** Logistic Regression + K-Means Clustering
- **Input features:** Historical occupancy, time patterns, nearby events
- **Output:** Probability of slot being occupied at a given time

---

## 🔥 Firebase Services Used

| Service | Usage |
|---|---|
| **Firestore** | Real-time slot availability, user profiles, booking records |
| **Firebase Auth** | Email/password, Google OAuth, phone OTP authentication |
| **Firebase Storage** | Parking space images, owner permit documents |
| **Firebase Hosting** | Static hosting for React build with global CDN |
| **Firebase Analytics** | Usage heatmaps, booking funnel tracking |

---

## 🚀 Deployment

### Deploy Frontend to Firebase Hosting

```bash
cd frontend
npm run build
firebase login
firebase init hosting
firebase deploy --only hosting
```

### Deploy Backend (Example: Google Cloud Run)

```bash
cd backend
gcloud run deploy parklink-api \
  --source . \
  --platform managed \
  --region asia-south1 \
  --allow-unauthenticated
```

---

## 🧪 Running Tests

```bash
# Backend tests
cd backend
pytest tests/ -v

# Frontend tests
cd frontend
npm test
```

---

## 🌐 Environment Variables Summary

| Variable | Location | Description |
|---|---|---|
| `FIREBASE_CREDENTIALS_PATH` | Backend `.env` | Path to service account JSON |
| `SECRET_KEY` | Backend `.env` | JWT signing key |
| `ALLOWED_ORIGINS` | Backend `.env` | CORS allowed origins |
| `REACT_APP_FIREBASE_*` | Frontend `.env` | Firebase client SDK config |
| `REACT_APP_BACKEND_URL` | Frontend `.env` | FastAPI backend base URL |

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m 'Add: your feature description'`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**ParkLink** — Built with Python, FastAPI, React JS, HTML, CSS, JavaScript, Firebase, Machine Learning & Scikit-learn.

> *Making urban parking smarter, one spot at a time.*
