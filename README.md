# AI Mock Interview Prep Application

An AI-powered preparation strategy platform designed to help candidates land their target jobs. The application analyzes a target **Job Description**, a candidate's **Resume** (PDF), and a **Self-Description** using Google Gemini AI to generate custom match scores, discover skill gaps, build a day-by-day study roadmap, and formulate typical technical/behavioral interview questions with answers. It can also automatically generate a tailored, ATS-friendly PDF resume matching the target job description.

---

## 🚀 Key Features

* **Resume Parsing**: Automatically extracts text from uploaded PDF resumes.
* **Match Score & Skill Gap Analysis**: Uses AI to assess how well your profile aligns with target job requirements and highlights critical skill gaps.
* **Personalized Prep Roadmaps**: Creates a day-by-day structured learning path.
* **Interview Q&A Prep**: Generates high-probability technical and behavioral interview questions customized to your profile, explaining the interviewer's intent and providing tips on how to answer them.
* **Tailored Resume PDF Generation**: Generates a professional, ATS-ready PDF resume specifically formatted for the target role using Puppeteer.
* **Modern Dashboard**: Responsive and premium dark-mode interface built with React and Sass.

---

## 🛠️ Tech Stack

### Backend
* **Core**: Node.js, Express.js (v5)
* **Database**: MongoDB (Mongoose Object Modeling)
* **AI Integration**: Google GenAI SDK (`@google/genai`)
* **File Uploads**: Multer (Memory Storage)
* **PDF Processing**: `pdf-parse` (Text extraction), `puppeteer` (HTML to PDF rendering)
* **Authentication**: JWT (JSON Web Tokens), `bcryptjs`, Cookie Parser

### Frontend
* **Core**: React (v19), Vite
* **Routing**: React Router (v7)
* **Styling**: Sass (CSS Preprocessor)
* **API Requests**: Axios

---

## 📂 Project Structure

```text
├── Backend/                 # Express REST API
│   ├── src/
│   │   ├── config/          # Database connection configs
│   │   ├── controllers/     # Route controllers (Auth, Interview reports)
│   │   ├── middlewares/     # Authentication & File-upload (multer) middlewares
│   │   ├── models/          # Mongoose Schemas (User, Blacklist, Reports)
│   │   ├── routes/          # Express API route declarations
│   │   └── services/        # Business logic & integrations (Gemini, Puppeteer)
│   ├── server.js            # Express Entrypoint
│   └── package.json         # Backend script & dependencies
│
└── Frontend/                # Vite React SPA
    ├── src/
    │   ├── features/
    │   │   ├── auth/        # Login/Register state, pages, and components
    │   │   └── interview/   # Dashboard, Profile, Roadmaps, and Q&A components
    │   ├── main.jsx         # App bootstrapping
    │   └── style.scss       # Global Sass variables & themes
    ├── index.html           # HTML Entrypoint
    └── package.json         # Frontend script & dependencies
```

---

## ⚙️ Getting Started

### Prerequisites
* **Node.js**: `v20.x` or later (Tested on `v24.x`)
* **MongoDB**: A local instance or a MongoDB Atlas connection string.
* **Google Gemini API Key**: Obtain a key from Google AI Studio.

---

### Step 1: Clone and Configure Backend
1. Navigate to the `Backend` directory:
   ```bash
   cd Backend
   ```
2. Install the server-side dependencies:
   ```bash
   npm install
   ```
3. Create a `.env` file in the `Backend` folder:
   ```env
   MONGO_URI=your_mongodb_connection_uri
   JWT_SECRET=your_secure_jwt_secret
   GOOGLE_GENAI_API_KEY=your_gemini_api_key
   ```
4. Start the backend development server (using `nodemon`):
   ```bash
   npm run dev
   ```
   *The server runs by default on **http://localhost:3000**.*

---

### Step 2: Configure and Start Frontend
1. Navigate to the `Frontend` directory:
   ```bash
   cd ../Frontend
   ```
2. Install the client-side dependencies:
   ```bash
   npm install
   ```
3. Start the Vite development server:
   ```bash
   npm run dev
   ```
   *The client runs by default on **http://localhost:5173**.*

---

## 🔗 Main API Endpoints

### Authentication
* `POST /api/auth/register` - Create a new user account.
* `POST /api/auth/login` - Authenticate a user and set access token cookie.
* `POST /api/auth/logout` - Invalidate the current session and clear cookies.

### Interview Strategy & Resume
* `POST /api/interview/` - Generate an interview strategy report (Accepts `multipart/form-data` with fields `jobDescription`, `selfDescription`, and `resume` PDF).
* `GET /api/interview/` - Fetch all recent interview reports for the logged-in user.
* `GET /api/interview/report/:interviewId` - Fetch details for a specific interview strategy report.
* `POST /api/interview/resume/pdf/:interviewReportId` - Generate a tailored PDF resume corresponding to a specific report.

---

## 📄 License
This project is licensed under the ISC License.
