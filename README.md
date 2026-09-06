# 🏥 Digital Hospital - Full Hospital Management System (HMS)

[![Continuous Integration](https://github.com/bedru-mekiyu/Digital-Hospital/actions/workflows/ci.yml/badge.svg)](https://github.com/bedru-mekiyu/Digital-Hospital/actions/workflows/ci.yml)
[![Node.js](https://img.shields.io/badge/Node.js-v18%2B-green.svg)](https://nodejs.org/)
[![React](https://img.shields.io/badge/React-v18-blue.svg)](https://react.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind--CSS-v3-38bdf8.svg)](https://tailwindcss.com/)
[![License: ISC](https://img.shields.io/badge/License-ISC-yellow.svg)](https://opensource.org/licenses/ISC)

A comprehensive, full-stack **Hospital Management System (HMS)** built with the **MERN stack** (MongoDB, Express.js, React, Node.js) and styled using **Tailwind CSS**.

The platform is divided into three distinct applications:
1. **Client Frontend**: A patient-facing portal for viewing hospital information, departments, doctors, services, and booking appointments.
2. **Dashboard Frontend**: An administrative portal for hospital administrators to manage doctors, staff, messages, appointments, and patient records.
3. **Backend Server**: A RESTful Express API handling authentication, role-based authorization, medical data persistence, file uploads via Cloudinary, and request logging.

---

## 📐 Architecture & Key Tech Stack

### 🛠️ Core Stack

- **Frontend Applications**: React 18, Vite, React Router DOM, Tailwind CSS, Lucide / React Icons, React Toastify, React Slick / Carousel.
- **Backend API**: Node.js, Express.js, Mongoose (MongoDB ORM), JWT Authentication, Cookie Parser, Bcrypt, Validator.
- **Media & File Handling**: Cloudinary SDK, Express FileUpload.
- **Quality & CI/CD**: ESLint, GitHub Actions CI Pipeline.

```
                  ┌──────────────────────┐
                  │   Patient Frontend   │ (Port 5173 / React + Vite)
                  └──────────┬───────────┘
                             │
                             ▼
┌──────────────────┐    ┌───────────┐    ┌───────────────────┐
│ Admin Dashboard  │───>│ REST API  │<───│ MongoDB Database  │
│(Port 5174 / React)    │ (Express) │    │                   │
└──────────────────┘    └─────┬─────┘    └───────────────────┘
                              │
                              ▼
                       ┌─────────────┐
                       │ Cloudinary  │ (Media Assets)
                       └─────────────┘
```

---

## 📁 Repository Structure

```
.
├── client/                 # Patient-facing React Web Application
│   ├── src/                # Components, pages, assets, and context
│   ├── eslint.config.js    # ESLint configuration
│   ├── vite.config.js      # Vite build configuration
│   └── package.json        # Dependencies & scripts
│
├── dashboard/              # Admin React Web Application
│   ├── src/                # Admin views (Doctor/Admin onboarding, Messages, Appointments)
│   ├── eslint.config.js    # ESLint configuration
│   ├── vite.config.js      # Vite build configuration
│   └── package.json        # Dependencies & scripts
│
├── server/                 # Node.js/Express Backend REST API
│   ├── controller/         # Request handling logic (User, Appointment, Message)
│   ├── middleware/         # Auth verification, Error handling
│   ├── model/              # Mongoose schemas (User, Appointment, Message)
│   ├── routes/             # API routes
│   ├── utils/              # JWT token generation
│   ├── server.js           # Express app setup and server entry point
│   ├── .env.example        # Environment variable configuration template
│   └── package.json        # Server dependencies & scripts
│
└── .github/
    └── workflows/
        └── ci.yml          # Automated CI pipeline for linting & building all modules
```

---

## ⚡ Features

### 👤 Patient Portal (`/client`)
- **Appointment Booking**: Schedule appointments with chosen doctors across departments.
- **Hospital Overview**: View available medical departments, services, and doctor profiles.
- **Inquiries**: Contact hospital administration directly via message forms.
- **Authentication**: Patient registration and login.

### 🛡️ Admin Dashboard (`/dashboard`)
- **Doctor Management**: Onboard new doctors with assigned departments, profile images, and bios.
- **Admin Management**: Register additional administrative accounts.
- **Messages Management**: Review and handle patient inquiry submissions.
- **Appointments Oversight**: Monitor and manage patient appointment statuses.

### 🔑 Backend API & Security (`/server`)
- **JWT Authentication & Authorization**: Secure cookie-based token authentication for Patients and Admins.
- **Image Cloud Storage**: Cloudinary integration for doctor profile images.
- **Global Error Handling**: Custom middleware for operational and validation error reporting.

---

## 🚀 Getting Started

### Prerequisites
- **Node.js**: `v18.x` or higher
- **npm**: `v9.x` or higher
- **MongoDB**: Local MongoDB instance (`mongodb://localhost:27017`) or MongoDB Atlas URI

---

## ⚙️ Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/bedru-mekiyu/Digital-Hospital.git
cd Digital-Hospital
```

### 2. Configure Environment Variables
Copy the example environment file in the `server` directory and fill in your credentials:

```bash
cp server/.env.example server/.env
```

Set appropriate values in `server/.env`:
```env
PORT=3030
MONGO_URL=mongodb://localhost:27017/hospital_management_system
JWT_EXPIRES=7d
FRONTEND_URL=http://localhost:5173
DASHBOARD_URL=http://localhost:5174
JWT_SECRET_KEY=your_jwt_secret_key
COOKIE_EXPIRE=7
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
```

---

### 3. Running Applications Locally

#### Start Backend Server
```bash
cd server
npm install
npm start
```
The server will start running on `http://localhost:3030`.

#### Start Patient Client
```bash
cd client
npm install
npm run dev
```
The client app will run on `http://localhost:5173`.

#### Start Admin Dashboard
```bash
cd dashboard
npm install
npm run dev
```
The dashboard app will run on `http://localhost:5174`.

---

## 🧪 Quality Assurance & Building

Each component of the repository is configured for code formatting, linting, and production builds:

```bash
# Client Quality Check
cd client
npm run lint
npm run build

# Dashboard Quality Check
cd dashboard
npm run lint
npm run build
```

---

## 🔄 CI/CD Pipeline

Automated testing and validation are handled via **GitHub Actions** (`.github/workflows/ci.yml`).

Every push or pull request to `main` or `master` automatically runs:
1. **Client Pipeline**: Dependency installation (`npm ci`), ESLint validation, and Vite production build.
2. **Dashboard Pipeline**: Dependency installation (`npm ci`), ESLint validation, and Vite production build.
3. **Server Pipeline**: Dependency installation (`npm ci`) and Node syntax verification.

---

## 📄 License

This project is licensed under the [ISC License](LICENSE).
