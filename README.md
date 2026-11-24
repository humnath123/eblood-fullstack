# 🩸 eBlood – Emergency Blood Donation and Management System

> **Find blood. Save lives.**

eBlood is a mobile application designed to improve blood donation coordination in Nepal. It connects **patients, donors, hospitals, blood banks and NGOs** on one platform, allowing users to find blood by blood group and location, send emergency requests and track responses.

This is a university Software Engineering project developed by a team of three students.

---

## 📑 Table of Contents

1. [Project Overview](#-project-overview)
2. [Project Objectives](#-project-objectives)
3. [Features](#-features)
4. [Technology Stack](#-technology-stack)
5. [System Architecture](#-system-architecture)
6. [Project Structure](#-project-structure)
7. [Current Project Status](#-current-project-status)
8. [Getting Started](#-getting-started)
9. [Environment Variables](#-environment-variables)
10. [Blood Request Workflow](#-blood-request-workflow)
11. [Security and Privacy](#-security-and-privacy)
12. [Team and Responsibilities](#-team-and-responsibilities)
13. [Git Workflow](#-git-workflow)
14. [Development Roadmap](#-development-roadmap)
15. [Documentation](#-documentation)
16. [Future Improvements](#-future-improvements)
17. [Disclaimer](#-disclaimer)

---

## 🎯 Project Overview

Finding compatible blood donors during emergencies can be difficult because information about donors, hospitals and blood banks is often scattered across different sources.

eBlood aims to address this problem by providing a centralized platform where patients can search for blood, submit emergency requests and connect with available donors and healthcare organizations.

The application focuses on accessibility, location-based discovery, privacy and efficient communication.

## 🎯 Project Objectives

- Develop a centralized blood donation coordination platform.
- Connect patients with available blood donors.
- Make emergency blood requests easier and faster.
- Enable blood searches based on blood group and geographical location.
- Help hospitals and blood banks manage blood-related requests.
- Encourage voluntary blood donation.
- Protect donor privacy and personal information.
- Provide an accessible interface in English and Nepali.

---

## ✨ Features

The following features represent the planned system functionality.

| User Role | Main Capabilities |
|---|---|
| Patient | Search blood, create emergency requests, track status, view donor responses and cancel requests |
| Donor | Set availability, view nearby requests, accept or decline requests, view donation history and next eligible date |
| Hospital | Manage profile, view and coordinate requests, update request status |
| Blood Bank | Manage blood inventory, blood groups, available units and inventory updates |
| NGO | Manage profiles, create donation camps and campaigns |
| Administrator | Manage users, verify hospitals and blood banks, review reports and monitor system activity |

### Additional Highlights

- Search priority: Nearby blood banks → Nearby hospitals → Eligible and available donors.
- Distance calculation using the Haversine formula.
- Location-based donor discovery.
- Donor exact location is not publicly displayed.
- Only approximate donor distance is displayed.
- OpenStreetMap integration.
- In-app notifications.
- English and Nepali language support.
- Blood donation history and availability management.

---

## 🛠️ Technology Stack

The project uses the following technologies.

| Layer | Technology |
|---|---|
| Frontend | Flutter, Dart |
| UI Framework | Material Design |
| State Management | Provider |
| Maps | flutter_map, OpenStreetMap |
| Backend | Node.js, Express.js |
| API Architecture | REST API |
| Authentication | JWT |
| Password Security | bcrypt |
| Input Validation | Joi |
| Database | Oracle Database Free |
| Database Driver | oracledb |
| Database Language | Oracle SQL |
| Development | Visual Studio Code |
| Mobile Development | Android Studio |
| API Testing | Postman |
| Version Control | Git and GitHub |
| UI Design | Figma |
| Diagrams | draw.io |

**Cost consideration:** The project is designed around free development tools and free software services. Hosting, messaging and external service costs may apply if the application is deployed beyond the local development environment.

---

## 🏗️ System Architecture

eBlood follows a client-server architecture.

### Backend Architecture

The backend separates API routing, request validation, authentication, controllers and business logic.

**Request flow:**

`Route → Middleware → Controller → Service → Oracle Database`

Responsibilities:

- Routes define API endpoints.
- Middleware handles authentication, authorization and validation.
- Controllers handle incoming requests and responses.
- Services contain application business logic.
- Oracle Database stores application data.

### Frontend Architecture

The Flutter application follows a layered structure.

**Request flow:**

`Screen → Provider → Repository → ApiClient → Backend API`

Responsibilities:

- Screens display application interfaces.
- Providers manage application state.
- Repositories handle data operations.
- ApiClient communicates with the backend.

---

## 📁 Project Structure

The following represents the intended project structure. Some folders and modules may still be under development.

```text
eBlood/
│
├── frontend/
│   └── eblood_app/
│       ├── lib/
│       │   ├── core/
│       │   │   ├── constants/
│       │   │   ├── theme/
│       │   │   ├── routes/
│       │   │   ├── network/
│       │   │   ├── localization/
│       │   │   └── utils/
│       │   │
│       │   ├── data/
│       │   │   ├── models/
│       │   │   ├── repositories/
│       │   │   └── api_client/
│       │   │
│       │   ├── providers/
│       │   ├── widgets/
│       │   │
│       │   └── screens/
│       │       ├── splash/
│       │       ├── auth/
│       │       ├── home/
│       │       ├── search/
│       │       ├── map/
│       │       ├── requests/
│       │       ├── patient/
│       │       ├── donor/
│       │       ├── hospital/
│       │       ├── blood_bank/
│       │       ├── ngo/
│       │       ├── admin/
│       │       ├── notifications/
│       │       └── profile/
│       │
│       └── pubspec.yaml
│
├── backend/
│   ├── server.js
│   ├── package.json
│   ├── .env.example
│   │
│   └── src/
│       ├── app.js
│       ├── config/
│       ├── routes/
│       ├── controllers/
│       ├── services/
│       ├── validators/
│       ├── middleware/
│       └── utils/
│
├── database/
│   ├── schema/
│   ├── seed/
│   ├── scripts/
│   └── tests/
│
├── docs/
│   ├── ERD/
│   ├── UML/
│   ├── API/
│   ├── wireframes/
│   ├── testing/
│   └── reports/
│
├── .gitignore
└── README.md
```

---

## 📊 Current Project Status

**Overall Status: Active Development**

eBlood has completed its initial planning, requirements analysis and technology selection. Development is currently progressing across the frontend, backend and database components.

### Development Progress

| Component | Current Status |
|---|---|
| Project proposal and requirements | Completed |
| Technology selection | Completed |
| Team organization | Completed |
| Initial system architecture | Designed |
| Flutter frontend | In Progress |
| Login interface | Initial development |
| Registration interface | In Progress |
| Node.js backend | Initial setup |
| Express middleware | In Progress |
| Joi validation | In Development |
| Oracle database | Selected; implementation pending verification |
| Database connectivity | Pending verification |
| REST API development | In Progress / Not yet confirmed |
| JWT authentication | Pending |
| Frontend-backend integration | Pending |
| Donor and patient modules | Planned |
| Blood request management | Planned |
| Hospital and blood bank modules | Planned |
| NGO and administrator modules | Planned |
| Maps and notifications | Planned |
| System testing | Planned |

### Recently Completed

- Initial project concept and requirements analysis.
- Selection of the technology stack.
- Three-member team organization.
- Initial Flutter application setup.
- Initial login interface development.
- Backend environment setup and architecture planning.
- Initial middleware and validation planning.

### Currently Working On

- Flutter frontend screen development.
- Login and registration UI.
- Node.js and Express backend organization.
- Backend validation and middleware.
- Oracle database preparation.
- Frontend and backend integration planning.

### Upcoming Tasks

- Complete authentication functionality.
- Establish Oracle database connectivity.
- Develop and test REST API endpoints.
- Implement JWT authentication and role-based access.
- Connect Flutter application with backend APIs.
- Develop patient and donor management.
- Implement emergency blood request functionality.
- Develop hospital and blood bank modules.
- Integrate maps and notifications.
- Perform testing and debugging.

*Note: Status descriptions reflect the currently confirmed development information. A feature should only be marked completed after its implementation and testing.*

---

## 🚀 Getting Started

Follow these instructions to set up the project locally.

### Prerequisites

Install the following tools:

- Flutter SDK 3.x – https://docs.flutter.dev/get-started/install
- Dart SDK – Included with Flutter
- Node.js 18 or newer – https://nodejs.org/
- Oracle Database Free – https://www.oracle.com/database/free/
- Android Studio – https://developer.android.com/studio
- Visual Studio Code – https://code.visualstudio.com/
- Git – https://git-scm.com/
- Postman – https://www.postman.com/

### 1. Clone the Repository

```bash
git clone https://github.com/humnath123/e-Blood-.git

cd e-Blood-
```

### 2. Set Up the Database

Navigate to the database directory:

```bash
cd database
```

The intended database setup process is:

1. Create the application database user.
2. Execute the SQL schema scripts in the correct order.
3. Insert sample data.
4. Verify tables, relationships and constraints.
5. Execute database tests.

Planned database script organization:

```text
database/
├── schema/
│   ├── 01_create_tables.sql
│   ├── 02_relationships.sql
│   ├── 03_constraints.sql
│   ├── 04_indexes.sql
│   ├── 05_sequences.sql
│   └── 06_views.sql
│
├── seed/
├── scripts/
└── tests/
```

Refer to `database/README.md` when available for the complete setup instructions.

### 3. Run the Backend

Open a terminal:

```bash
cd backend
npm install
```

Create the environment configuration file:

```bash
```

Copy `.env.example` to `.env` and configure the required values.

Start the development server:

```bash
npm run dev
```

The development health endpoint is intended to be:

```text
http://localhost:3000/api/health
```

### 4. Run the Flutter Application

Open another terminal:

```bash
cd frontend/eblood_app
```

Install dependencies:

```bash
flutter pub get
```

Run the application:

```bash
flutter run
```

If the Android platform folder has not yet been created, initialize it once:

```bash
flutter create . --platforms=android
```

### 5. Connect Flutter to the Backend

For Android emulator development, the host computer is accessible through:

```text
http://10.0.2.2:3000
```

For a physical Android phone, use your computer's local Wi-Fi IP address.

Example:

```text
http://192.168.1.10:3000
```

The API base URL should be configured in the application's network configuration.

---

## 🔐 Environment Variables

The backend uses environment variables to protect sensitive configuration.

Create:

`backend/.env`

Example configuration:

```env
PORT=3000
NODE_ENV=development

DB_USER=eblood_app
DB_PASSWORD=change_me
DB_CONNECT_STRING=localhost:1521/FREEPDB1

JWT_SECRET=use_a_long_random_secret
JWT_EXPIRES_IN=1d
```

**Security rules:**

- Never commit `.env` to GitHub.
- Never expose database passwords.
- Never store JWT secrets in Flutter source code.
- Keep `.env.example` free of real credentials.
- Use strong secrets for production.
- Configure HTTPS for deployed environments.

---

## 🩸 Blood Request Workflow

The proposed blood request workflow is:

1. Patient creates an emergency blood request.
2. Backend validates the submitted information.
3. The request is stored in the database.
4. Nearby blood banks and hospitals are identified.
5. Eligible and available donors are identified.
6. Matching donors receive notifications.
7. Donors accept or decline the request.
8. Patient views donor responses.
9. Hospital or blood bank coordinates the process.
10. Request status is updated.
11. Confirmed donations are recorded in donation history.

### Request Status

```text
Pending
   |
   v
Accepted
   |
   v
In Progress
   |
   v
Fulfilled
```

A request may also be marked as:

```text
Cancelled
```

---

## 🔒 Security and Privacy

Security and privacy are important parts of eBlood.

The planned security mechanisms include:

| Security Component | Implementation |
|---|---|
| Password protection | bcrypt hashing |
| Authentication | JWT |
| Authorization | Role-based access control |
| Input validation | Joi |
| Configuration | Environment variables |
| Communication | HTTPS in production |
| Error handling | Safe error responses |
| Location privacy | Approximate distance only |

### Privacy Principles

- Donors' exact locations must not be publicly exposed.
- Personal information should only be accessible to authorized users.
- Passwords must never be stored as plain text.
- API endpoints must validate incoming data.
- Sensitive information must not appear in application logs.

---

## 👥 Team and Responsibilities

The project is developed by a team of three students.

| Member | Main Responsibilities |
|---|---|
| Person 1 | Project Manager, Flutter frontend, UI design, integration and documentation |
| Person 2 | Node.js backend, REST APIs, authentication, validation and security |
| Person 3 | Oracle database, ER diagram, SQL schema, constraints, indexes and database testing |

### Shared Responsibilities

All team members participate in:

- System integration.
- Testing and debugging.
- Requirement discussions.
- Code reviews.
- Documentation.
- Final project demonstration.

---

## 🌿 Git Workflow

The project uses Git and GitHub for version control and team collaboration.

### Main Branch

`main` is reserved for stable and tested code.

### Feature Branches

Examples:

```bash
git checkout -b feature/auth-api

git checkout -b feature/donor-search-ui

git checkout -b feature/patient-dashboard

git checkout -b db/inventory-tables
```

### Save and Push Changes

```bash
git add .

git commit -m "Add login validation"

git push origin feature/auth-api
```

### Collaboration Guidelines

1. Pull the latest changes before starting new work.
2. Create separate feature branches.
3. Write meaningful commit messages.
4. Test your changes before pushing.
5. Create a pull request.
6. Get at least one teammate's review.
7. Merge only after reviewing and testing.

To update your local main branch:

```bash
git checkout main
git pull origin main
```

---

## 📅 Development Roadmap

The project will be developed incrementally.

- [x] **Stage 1** – Project concept, proposal and requirements analysis.
- [x] **Stage 2** – Technology selection, team organization and initial architecture.
- [ ] **Stage 3** – Flutter frontend development and UI completion.
- [ ] **Stage 4** – Node.js and Express backend development.
- [ ] **Stage 5** – Oracle Database schema and connectivity.
- [ ] **Stage 6** – REST API development and backend validation.
- [ ] **Stage 7** – Authentication, registration, login and role management.
- [ ] **Stage 8** – Flutter and backend integration.
- [ ] **Stage 9** – Patient and donor management modules.
- [ ] **Stage 10** – Emergency blood request and donor matching system.
- [ ] **Stage 11** – Hospital, blood bank and inventory management.
- [ ] **Stage 12** – NGO campaigns and administrator dashboard.
- [ ] **Stage 13** – OpenStreetMap integration and notifications.
- [ ] **Stage 14** – Testing, debugging, documentation and final demonstration.

---

## 📚 Documentation

Project documentation will be maintained in the `docs/` directory.

| Documentation | Location |
|---|---|
| Entity Relationship Diagram | `docs/ERD/` |
| UML Diagrams | `docs/UML/` |
| API Documentation | `docs/API/` |
| Postman Collection | `docs/API/` |
| UI Wireframes | `docs/wireframes/` |
| Test Plan | `docs/testing/` |
| Project Report | `docs/reports/` |

---

## 🔮 Future Improvements

Potential future enhancements include:

- Advanced donor matching.
- Improved emergency notification delivery.
- Blood inventory availability updates.
- Better location-based search.
- Donation camp registration.
- Analytics and reporting dashboard.
- Improved accessibility.
- Additional language support.
- Deployment and production monitoring.

---

## ⚕️ Disclaimer

eBlood is a blood donation coordination platform developed for educational purposes.

Donor eligibility information displayed in the application is guidance only and does not replace professional medical advice.

Blood donation eligibility, compatibility and transfusion decisions must always be confirmed by qualified medical professionals.

---

## ❤️ Our Vision

We believe technology can help make blood donation coordination easier and more accessible.

Our goal is to connect people who need blood with those willing to donate and to support a more organized blood donation ecosystem in Nepal.

**eBlood – Find Blood. Save Lives. Every Drop Matters.**