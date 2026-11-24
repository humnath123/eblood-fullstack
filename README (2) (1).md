# eBlood – Emergency Blood Donation and Management System

> Find blood. Save lives.

eBlood is a mobile application that improves blood donation coordination in Nepal. It connects **patients, donors, hospitals, blood banks and NGOs** on one platform, so people can find blood by blood group and location, send emergency requests and track responses.

This is a university software engineering project built by a team of three students.

---

## Table of Contents
1. [Features](#features)
2. [Tech Stack](#tech-stack)
3. [Project Structure](#project-structure)
4. [Getting Started](#getting-started)
5. [Environment Variables](#environment-variables)
6. [Blood Request Workflow](#blood-request-workflow)
7. [Security and Privacy](#security-and-privacy)
8. [Team and Responsibilities](#team-and-responsibilities)
9. [Git Workflow](#git-workflow)
10. [Development Roadmap](#development-roadmap)
11. [Documentation](#documentation)
12. [Disclaimer](#disclaimer)

---

## Features

| Role | Main capabilities |
|---|---|
| **Patient** | Search blood, create emergency requests, track status, view donor responses, cancel requests |
| **Donor** | Set availability, view nearby requests, accept or decline, donation history, next eligible date |
| **Hospital** | Manage profile, view and coordinate requests, update request status |
| **Blood Bank** | Manage inventory (group, units, last updated), view requests |
| **NGO** | Manage profile, create donation camps and campaigns |
| **Administrator** | Manage users, verify hospitals and blood banks, review reports, view system activity |

Other highlights:
- Search priority: **nearby blood banks → nearby hospitals → eligible and available donors**
- Distance calculated with the **Haversine formula**
- Donor exact location is never shown publicly; only approximate distance
- Maps with OpenStreetMap, in-app notifications, English and Nepali labels

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Flutter, Dart, Material Design, Provider, flutter_map, OpenStreetMap |
| Backend | Node.js, Express.js, REST API, JWT, bcrypt, Joi |
| Database | Oracle Database Free, Oracle SQL, `oracledb` driver |
| Tools | VS Code, Android Studio, Git/GitHub, Postman, draw.io, Figma |

Only free tools and services are used. No paid APIs or hosting are required.

## Project Structure

```text
eBlood/
├── frontend/eblood_app/        Flutter mobile app
│   └── lib/
│       ├── core/               constants, theme, routes, network, localization, utils
│       ├── data/               models, repositories, api_client
│       ├── providers/          app state (Provider)
│       ├── widgets/            reusable UI components
│       └── screens/            splash, auth, home, search, map, requests,
│                               patient, donor, hospital, blood_bank, ngo, admin,
│                               notifications, profile
├── backend/                    Node.js + Express REST API
│   ├── server.js               starts the server
│   └── src/
│       ├── app.js              Express setup
│       ├── config/             Oracle connection, env, firebase
│       ├── routes/             endpoint definitions
│       ├── controllers/        handle request and response
│       ├── services/           business logic and database queries
│       ├── validators/         Joi validation rules
│       ├── middleware/         auth, roles, validation, error handling
│       └── utils/              haversine, jwt, password, response helpers
├── database/
│   ├── schema/                 01 tables → 06 views (run in order)
│   ├── seed/                   sample data
│   ├── scripts/                create user, run_all, drop_all
│   └── tests/                  constraint and query tests
├── docs/                       ERD, API, UML, wireframes, testing, reports
├── .gitignore
└── README.md
```

**How the code flows**
- Backend: `route → middleware → controller → service → Oracle`
- Frontend: `screen → provider → repository → ApiClient → backend`

## Getting Started

### Prerequisites
- [Flutter SDK](https://docs.flutter.dev/get-started/install) (3.x) and Android Studio with an emulator
- [Node.js](https://nodejs.org/) 18 or newer
- [Oracle Database Free](https://www.oracle.com/database/free/) with SQL*Plus or SQL Developer
- Git and Postman

### 1. Clone the repository
```bash
git clone <your-repository-url>
cd eBlood
```

### 2. Set up the database
```bash
cd database
# 1. Create the application user (see scripts/00_create_app_user.sql)
# 2. Run the scripts in order:
#    schema/01_create_tables.sql … schema/06_views.sql
#    seed/01_… … seed/04_…
```
See `database/README.md` for details.

### 3. Run the backend
```bash
cd backend
npm install
cp .env.example .env      # then fill in your own values
npm run dev
```
Check it works: open `http://localhost:3000/api/health`

### 4. Run the Flutter app
```bash
cd frontend/eblood_app
flutter create . --platforms=android    # first time only
flutter pub get
flutter run
```
The Android emulator reaches your computer at `http://10.0.2.2:3000`.
On a real phone, set `apiBaseUrl` in `lib/core/constants/app_constants.dart` to your computer's Wi-Fi IP (for example `http://192.168.1.10:3000/api`).

## Environment Variables

Copy `backend/.env.example` to `backend/.env`. **Never commit `.env`.**

```env
PORT=3000
NODE_ENV=development

DB_USER=eblood_app
DB_PASSWORD=change_me
DB_CONNECT_STRING=localhost:1521/FREEPDB1

JWT_SECRET=use_a_long_random_string
JWT_EXPIRES_IN=1d
```

Database credentials and secrets must never appear in Flutter code or on GitHub.

## Blood Request Workflow

1. Patient creates a blood request
2. Backend validates it (duplicates and invalid data are rejected)
3. Request is saved in Oracle
4. Matching blood banks, hospitals and donors are identified
5. Eligible and available donors are notified
6. Donors accept or decline
7. Patient views the responses
8. Hospital or blood bank coordinates
9. Status is updated: `Pending → Accepted → In Progress → Fulfilled` (or `Cancelled`)
10. Confirmed donations are saved to donation history

## Security and Privacy

- Passwords hashed with **bcrypt**, never stored as plain text
- **JWT** authentication and **role-based access control**
- Input validation with **Joi**
- Secrets kept in environment variables
- HTTPS for any deployed environment
- Minimal personal data; donor location is approximate only
- Safe error messages that never reveal internal details

## Team and Responsibilities

| Member | Responsibilities |
|---|---|
| **Person 1** | Project management, Flutter frontend, UI design, integration, documentation |
| **Person 2** | Node.js backend, REST APIs, authentication, validation, security |
| **Person 3** | Oracle database, ER diagram, SQL schema, constraints, indexes, database testing |

All members take part in integration, testing and debugging.

## Git Workflow

- `main` is always stable and working
- Work on feature branches: `feature/auth-api`, `feature/donor-search-ui`, `db/inventory-tables`
- Open a pull request and get one teammate's review before merging
- Write clear commit messages, for example `Add login validation`

## Development Roadmap

- [x] **Stage 1** – Project folders and Flutter frontend structure
- [ ] **Stage 2** – Backend setup, Oracle connection, `/api/health`
- [ ] **Stage 3** – Connect Flutter to the backend
- [ ] **Stage 4** – Authentication (register, login, roles, forgot password)
- [ ] **Stage 5** – Donor and patient modules
- [ ] **Stage 6** – Blood request workflow and matching
- [ ] **Stage 7** – Hospital and blood bank modules, inventory
- [ ] **Stage 8** – NGO campaigns and admin module
- [ ] **Stage 9** – Maps and notifications
- [ ] **Stage 10** – Testing, documentation and final demo

## Documentation

| Item | Location |
|---|---|
| ER diagram | `docs/ERD/` |
| UML diagrams | `docs/UML/` |
| API documentation and Postman collection | `docs/API/` |
| Wireframes | `docs/wireframes/` |
| Test plan | `docs/testing/` |
| Project report | `docs/reports/` |

## Disclaimer

eBlood is a coordination tool. Donor eligibility information shown in the app is **guidance only** and does not replace medical advice. Eligibility must always be confirmed by a qualified medical professional.
