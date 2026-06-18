# Quiz Application

A full-stack web application for taking knowledge quizzes, featuring user authentication and a scoreboard with top results. The project is built using **Node.js/Express** on the backend, **SQLite** as the database, and **React** on the frontend.

## 🚀 Technologies

### Backend
- Node.js & Express.js – Core runtime and REST API architecture
- SQLite3 – Lightweight relational database for storing users, questions, and results
- JSON Web Tokens (JWT) – Secure user authentication via tokens
- Bcrypt – Password hashing and protection
- CORS – Enables cross-origin resource sharing between frontend and backend

### Frontend
- React (functional components & Hooks) – User interface
- React Router DOM – Client-side routing and navigation
- React Context API – Global authentication state management
- Fetch API – Communication with backend services


# Quiz Application

Full-stack veb aplikacija za polaganje kvizova znanja, sa sistemom autentifikacije korisnika i rang listom (scoreboard) najboljih rezultata. Projekat je izgrađen korišćenjem **Node.js/Express** tehnologija na backend-u, **SQLite** baze podataka i **React** biblioteke na frontend-u.

---

## 🚀 Tehnologije

### Backend
* **Node.js** & **Express.js** – Pokretački algoritam i REST API arhitektura
* **SQLite3** – Lagana relaciona baza podataka za čuvanje korisnika, pitanja i rezultata
* **JSON Web Tokens (JWT)** – Bezbedna autentifikacija korisnika putem tokena
* **Bcrypt** – Heširanje i zaštita korisničkih lozinki
* **CORS** – Omogućavanje cross-origin deljenja resursa sa frontend-om

### Frontend
* **React** (sa funkcionalnim komponentama i Hooks) – Korisnički interfejs
* **React Router DOM** – Klijentsko rutiranje i navigacija unutar aplikacije
* **React Context API** – Globalno upravljanje stanjem autentifikacije korisnika
* **Fetch API** – Komunikacija sa backend servisima

---

## 📂 Struktura Projekta

Ovde je tačna struktura direktorijuma i fajlova na osnovu koda aplikacije:

```text
├── backend/
│   ├── database/
│   │   └── quiz.db             # SQLite baza podataka
│   ├── src/
│   │   ├── config/
│   │   │   ├── db.js           # Konekcija sa SQLite bazom
│   │   │   └── jwt.js          # JWT konfiguracija i tajni ključ ("12345")
│   │   ├── controllers/
│   │   │   ├── authController.js   # Logika za registraciju i login
│   │   │   ├── quizController.js   # Logika za kviz (start i submit)
│   │   │   └── scoreController.js  # Logika za dobavljanje rang liste
│   │   ├── middleware/
│   │   │   └── authMiddleware.js   # Middleware za verifikaciju JWT tokena
│   │   ├── models/
│   │   │   ├── QuestionModel.js    # SQL upiti za pitanja (RANDOM i provera)
│   │   │   └── UserModel.js        # SQL upiti za korisnike (create i find)
│   │   └── routes/
│   │       ├── authRoutes.js       # Rute za autentifikaciju
│   │       ├── quizRoutes.js       # Rute za kviz operacije
│   │       └── scoreRoutes.js      # Rute za rang listu
│   └── app.js                  # Glavni Express app fajl (izvan src/ foldera)
│
├── frontend/
│   ├── src/
│   │   ├── api/
│   │   │   └── api.js          # API klijent za Fetch pozive ka backend-u
│   │   ├── components/
│   │   │   ├── Login.js        # Stranica za prijavu korisnika
│   │   │   ├── Register.js     # Stranica za registraciju
│   │   │   ├── Quiz.js         # Komponenta za upravljanje tokom kviza
│   │   │   ├── Question.js     # Prikaz pojedinačnog pitanja i opcija
│   │   │   └── Scoreboard.js   # Prikaz top 20 rezultata
│   │   ├── context/
│   │   │   └── AuthContext.js  # Kontekst i Provider za login/logout stanje
│   │   ├── App.js              # Definicija klijentskih ruta i AuthProvider-a
│   │   └── index.js            # Ulazna tačka React aplikacije
```

## 🔌 API Routes

All routes except authentication are protected by authMiddleware.js and require: Authorization: Bearer <token>

Authentication (/api/auth)
POST /register – Register a new user (password hashing + token generation)
POST /login – Authenticate user and return JWT token

Quiz (/api/quiz)
GET /start – Fetch 10 random questions from the database
POST /submit – Submit answers, calculate score, and store results in quiz_results

Scoreboard (/api/scores)
GET / – Retrieve top 20 results with usernames and scores



## 💻 How to Run the Project Locally

Prerequisites: Make sure you have Node.js installed.

Backend Setup:
cd backend
npm install express cors sqlite3 jsonwebtoken bcrypt
node src/app.js

Or if using nodemon:
npm run dev

Frontend Setup:
cd frontend
npm install react-router-dom
npm start

App runs at:
http://localhost:3000

## 🔐 Security Notes

JWT secret key is currently hardcoded in config/jwt.js as "12345".
For production, move it to .env using process.env.JWT_SECRET.
User session is stored in localStorage to persist login state after refresh.

## 📌 Features

User registration and login
Secure authentication using JWT
Dynamic quiz with random questions
Score calculation and storage
Leaderboard (top 20 players)
Protected API routes
Responsive React UI

## 🛠️ Future Improvements

Add timed quizzes
Add categories / difficulty levels
Improve UI/UX design
Add admin panel for question management
Deploy backend & frontend to cloud (Render / Vercel)