# 🤖 Job Portal with AI-Powered Resume Filtering

A full-stack Job Portal application that connects job seekers with employers and adds intelligent resume screening to the recruitment workflow.

Candidates can create accounts, browse/apply for jobs, submit resumes, and track applications. Employers can manage job opportunities, review applicants, filter candidates by skills, and use resume match scores to identify suitable candidates faster.

🔗 **Live Backend API:** https://job-portal-backend-m74d.onrender.com

🔗 **GitHub:** https://github.com/Aafrin777/resumefilter_react

---

## 📌 Project Overview

This project was built to demonstrate a complete full-stack recruitment workflow using **React.js, Node.js, Express.js, MongoDB, JWT authentication, Multer, and NLP-based resume parsing**.

The application has two main user experiences:

### 👤 Job Seekers

- Register and log in securely
- Browse job opportunities
- Apply for jobs
- Upload resumes in PDF format
- Provide skills, education, phone number, and experience
- View application information
- Receive resume skill-match results

### 🏢 Employers / HR

- Authenticate securely
- Create and manage job opportunities
- View candidate applications
- Review uploaded resumes
- Filter candidates by skills
- View matched skills and resume match scores
- Shortlist suitable candidates
- Export application data to Excel or PDF

---

## ✨ Key Features

### 🔐 Authentication & Authorization

- User registration and login
- JWT-based authentication
- Password hashing with bcryptjs
- Role-based access for job seekers and employers
- Protected API routes
- Persistent login information on the frontend
- Duplicate email validation
- Server-side request validation

### 💼 Job Portal

- Job listing interface
- Job application workflow
- Candidate and employer experiences
- Application management
- Employer applicant dashboard

### 📄 Resume Upload

- PDF resume upload using Multer
- Resume files stored on the backend
- Resume viewing through the backend
- Candidate information stored in MongoDB
- Application records linked with user data

### 🤖 AI-Assisted Resume Filtering

The project includes a rule-based/NLP-assisted resume screening workflow.

When a candidate submits a resume:

1. The PDF is uploaded.
2. Resume text is extracted.
3. Relevant skills are identified.
4. Candidate skills are compared with desired skills.
5. A match score is calculated.
6. Matched skills are stored with the application.
7. Employers can use the results to identify stronger matches.

> **Note:** The current implementation uses text extraction and skill-matching logic rather than a machine-learning model. It is therefore more accurate to describe the feature as **AI-assisted / NLP-based resume screening** rather than claiming a trained ML model.

### 🔎 Candidate Filtering

Employers can filter applications using recruitment criteria such as:

- Skills
- Experience
- Education
- Resume match score
- Matched skills

### 📊 Application Management

- View all applications
- Review candidate details
- View resumes
- Inspect matched skills
- Review screening scores
- Shortlist candidates
- Export application information

### 📥 Data Export

Application information can be exported as:

- Excel (`.xlsx`)
- PDF (`.pdf`)

---

# 🛠️ Tech Stack

## Frontend

- **React.js** — Component-based user interface
- **Axios** — HTTP requests to the backend API
- **React Router DOM** — Client-side routing
- **CSS / Tailwind CSS** — Responsive styling and UI
- **JavaScript (ES6+)** — Application logic

## Backend

- **Node.js** — JavaScript runtime
- **Express.js** — REST API and server framework
- **Mongoose** — MongoDB ODM
- **MongoDB** — Database
- **JWT (JSON Web Token)** — Authentication
- **bcryptjs** — Password hashing
- **Multer** — Resume file uploads
- **pdf-parse** — PDF text extraction
- **dotenv** — Environment variable management
- **CORS** — Frontend/backend communication

## Data Export

- **xlsx** — Excel export
- **jsPDF** — PDF generation
- **jsPDF AutoTable** — PDF table generation

## Development & Deployment

- **Git** — Version control
- **GitHub** — Source code hosting
- **Render** — Backend deployment
- **MongoDB Atlas / MongoDB** — Database hosting
- **Thunder Client / Postman** — API testing
- **Nodemon** — Development server auto-restart

---

# 🏗️ Application Architecture

The project follows a layered backend architecture:

```text
React Frontend
      │
      │ Axios / HTTP Requests
      ▼
Express.js API
      │
      ├── Routes
      │     ├── Authentication
      │     ├── Applications
      │     └── Protected Routes
      │
      ▼
Controllers
      │
      ▼
Middleware
      │
      ├── JWT Authentication
      └── Multer File Upload
      │
      ▼
Mongoose Models
      │
      ▼
MongoDB
```

### Backend Layer Responsibilities

| Layer | Responsibility | Example |
|---|---|---|
| Route | Defines API endpoints | `authRoutes.js` |
| Controller | Contains application/business logic | `authController.js` |
| Model | Defines MongoDB schemas | `User.js` |
| Middleware | Authentication, authorization and uploads | `authMiddleware.js`, `upload.js` |
| Server | Starts Express and connects services | `server.js` |

---

# 📁 Project Structure

The project is organized into separate frontend and backend applications:

```text
resumefilter_react/
│
├── client/                         # React frontend
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Navbar
│   │   │   ├── Hero
│   │   │   ├── Features
│   │   │   └── Footer
│   │   │
│   │   ├── pages/
│   │   │   ├── Login
│   │   │   ├── Register
│   │   │   ├── ApplicationForm
│   │   │   └── AllApplications
│   │   │
│   │   ├── App.js
│   │   ├── api.js
│   │   └── index.css
│   │
│   ├── package.json
│   └── .gitignore
│
├── job-portal/                     # Node.js / Express backend
│   ├── controllers/
│   │   └── authController.js
│   │
│   ├── middleware/
│   │   ├── authMiddleware.js
│   │   └── upload.js
│   │
│   ├── models/
│   │   ├── User.js
│   │   └── Application.js
│   │
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── protectedRoutes.js
│   │   └── Application_2.js
│   │
│   ├── uploads/                    # Uploaded resumes
│   ├── server.js
│   └── package.json
│
├── .gitignore
└── README.md
```

> File names can evolve as the project is maintained; the structure above describes the main architecture and responsibilities.

---

# 🔄 Authentication Flow

```text
User
 │
 ▼
React Register/Login Form
 │
 ▼
Axios Request
 │
 ▼
Express Authentication Route
 │
 ▼
authController.js
 │
 ├── Validate input
 ├── Check existing user
 ├── Hash password
 └── Generate JWT
 │
 ▼
MongoDB
 │
 ▼
JWT returned to frontend
 │
 ▼
Protected API Requests
 │
 ▼
authMiddleware.js
 │
 ▼
Authorized Route
```

---

# 📄 Resume Screening Flow

```text
Candidate
   │
   ▼
Application Form
   │
   ├── Personal Information
   ├── Skills
   ├── Experience
   ├── Education
   └── PDF Resume
          │
          ▼
       Multer
          │
          ▼
    Resume Storage
          │
          ▼
     PDF Text Extraction
          │
          ▼
      Skill Matching
          │
          ├── Matched Skills
          └── Match Score
                  │
                  ▼
              MongoDB
                  │
                  ▼
           Employer Dashboard
                  │
                  ▼
          Candidate Filtering
```

---

# 🧠 Resume Matching Logic

The screening system is designed to reduce manual resume review.

A simplified workflow is:

```text
Resume Text
     +
Required / Desired Skills
     ↓
Normalize Skill Names
     ↓
Compare Skills
     ↓
Identify Matched Skills
     ↓
Calculate Match Score
     ↓
Store Screening Results
```

The application stores screening information with the candidate application so employers can quickly compare applicants.

---

# 🔌 API Overview

The backend exposes REST-style endpoints for authentication and application management.

### Authentication

```text
POST /api/auth/register
POST /api/auth/login
```

### Protected Resources

Protected routes require a valid JWT token.

```text
Authorization: Bearer <token>
```

### Applications

The application includes endpoints for:

- Creating candidate applications
- Uploading resumes
- Retrieving applications
- Filtering candidates
- Accessing application details

> Endpoint names may vary depending on the current route implementation.

---

# ⚙️ Environment Variables

Environment variables are required for local development and deployment.

Example backend configuration:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secure_jwt_secret
```

Frontend configuration should contain the backend API URL required by the React application.

### 🔒 Security

**Never commit `.env` files to GitHub.**

The project uses `.gitignore` to keep environment files out of version control.

Use an example file when documenting required variables:

```env
MONGO_URI=
JWT_SECRET=
PORT=
```

---

# 🚀 Running the Project Locally

## 1. Clone the repository

```bash
git clone https://github.com/Aafrin777/resumefilter_react.git
cd resumefilter_react
```

## 2. Install backend dependencies

```bash
cd job-portal
npm install
```

Create the backend `.env` file with your local configuration.

## 3. Start the backend

```bash
nodemon server.js
```

or:

```bash
node server.js
```

The backend runs locally on:

```text
http://localhost:5000
```

## 4. Install frontend dependencies

Open another terminal:

```bash
cd client
npm install
```

Create the required frontend environment configuration if the current frontend expects one.

## 5. Start the React application

```bash
npm start
```

The frontend will normally run on:

```text
http://localhost:3000
```

---

# 🧪 API Testing

The backend APIs were tested during development using tools such as:

- Thunder Client
- Postman

Example registration request:

```http
POST /api/auth/register
Content-Type: application/json
```

```json
{
  "name": "Test User",
  "email": "test@example.com",
  "password": "123456",
  "role": "user"
}
```

Example login request:

```http
POST /api/auth/login
Content-Type: application/json
```

---

# ☁️ Deployment

The backend is deployed on **Render**.

🔗 **Production Backend:** https://job-portal-backend-m74d.onrender.com

The frontend can be deployed separately using a static hosting platform such as Vercel or Netlify.

For production deployment:

1. Push the project to GitHub.
2. Create a backend web service on Render.
3. Configure the required environment variables in Render.
4. Set the correct build/start commands.
5. Deploy the React frontend separately.
6. Update the frontend API URL to point to the production backend.

### Production Environment Variables

Production secrets should be configured through the hosting provider's environment-variable settings rather than committed to GitHub.

---

# 🛡️ Security Practices

The project includes several common backend security practices:

- Password hashing with bcryptjs
- JWT-based authentication
- Protected routes
- Role-based authorization
- Environment variables for secrets
- CORS configuration
- Server-side validation
- `.env` files excluded from Git
- Uploaded resume handling through Multer

> Production systems should additionally use secure cookies/token storage strategies, strict CORS policies, rate limiting, file-type/size validation, malware scanning, HTTPS, and other appropriate security controls.

---

# 📚 What I Learned

This project helped demonstrate practical full-stack development concepts including:

- Building REST APIs with Express.js
- Designing MongoDB schemas with Mongoose
- Implementing JWT authentication
- Hashing passwords securely
- Creating protected routes and middleware
- Connecting React applications to REST APIs
- Handling multipart/form-data and PDF uploads
- Extracting text from uploaded documents
- Implementing skill-based resume matching
- Managing role-based application workflows
- Exporting data to Excel and PDF
- Deploying a Node.js backend
- Managing environment variables securely
- Organizing a full-stack application using layered architecture

---

# 🎯 Future Improvements

Possible future enhancements include:

- Machine-learning based resume classification
- Semantic similarity using embeddings
- Job recommendation system
- Advanced recruiter analytics
- Candidate ranking
- Email notifications
- Cloud resume storage
- Resume preview inside the dashboard
- Advanced search and filtering
- Interview scheduling
- Recruiter-specific dashboards
- Automated candidate recommendations

---

# 👩‍💻 Author

**Aafrin**

GitHub: https://github.com/Aafrin777

---

## ⭐ Project Highlights

**Full-Stack Development • React.js • Node.js • Express.js • MongoDB • JWT Authentication • Resume Upload • NLP-Based Resume Screening • Skill Matching • REST APIs • Role-Based Access Control • Data Export • Render Deployment**
