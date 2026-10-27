# NeuroGuard - Gait & Neurological Motor Assessment System

NeuroGuard is an AI-assisted neurological screening and motor assessment application designed for early detection and tracking of motor symptoms associated with Parkinson's Disease and related movement disorders.

## Features

- **Finger Tapping Assessment**:
  - Live kinematic waveform tracking using MediaPipe Vision.
  - Frequency, amplitude, and rhythmicity analysis.
  - Automated scoring based on trained tapping kinematic models.

- **Tremor Detection**:
  - Real-time facial and extremity tremor tracking.
  - Fast Fourier Transform (FFT) spectrum analysis for tremor frequency peak detection.

- **Gait Analysis**:
  - Full-body skeleton tracking and joint kinematic angle calculation.
  - Stride symmetry, cadence, velocity, and gait irregularity detection.
  - Preloaded sample test video verification mode.

- **Comprehensive Motor & Cognitive Battery**:
  - Sit-to-Stand Test
  - Postural Stability Test
  - Toe Tapping Test
  - Spiral Drawing Test
  - Clock Drawing Test
  - Attention & Memory screening

## Tech Stack

- **Frontend**: React 18, Vite
- **Computer Vision & ML**: MediaPipe Tasks Vision (`@mediapipe/tasks-vision`)
- **Signal Processing**: Custom FFT & kinematic analysis utilities
- **Styling**: Modern dark-mode responsive UI

## Getting Started

### Prerequisites
- **Node.js**: v18.0.0 or higher ([Download Node.js](https://nodejs.org/))
- **npm**: v9.0.0 or higher (comes bundled with Node.js)
- Modern web browser with webcam access (Chrome, Edge, or Firefox recommended)

---

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/vikasvikasgl-oss/major_project_7thsem.git
   cd major_project_7thsem
   ```

2. **Install dependencies:**
   Navigate into the application package directory and install packages:
   ```bash
   cd finger_tapping_test_final/tremor
   npm install
   ```

---

### How to Run the Project

The application requires **both** the backend API server (port `5000`) and the Vite frontend (port `5173`) to run concurrently.

#### Method 1: Running from the Root Directory (Recommended)
From the root repository folder (`major_project_7thsem`), open two terminal windows:

* **Terminal 1: Start the Backend Server (Express + SQLite)**
  ```bash
  npm run server
  ```
  > Runs the Express API on `http://localhost:5000` for user authentication, patient vitals, and SQLite logging.

* **Terminal 2: Start the Frontend Application (Vite + React)**
  ```bash
  npm run dev
  ```
  > Starts the Vite development server on `http://localhost:5173`.

---

#### Method 2: Running from the Application Subfolder
Alternatively, navigate directly to `finger_tapping_test_final/tremor`:

```bash
cd finger_tapping_test_final/tremor

# Terminal 1: Run Backend API
node server.js

# Terminal 2: Run Frontend
npm run dev
```

---

### Accessing the Application

1. Open your browser and navigate to:
   ```
   http://localhost:5173
   ```
2. **Demo Patient Login**:
   - Click the **"Demo Patient Login"** button on the screen, or log in manually with:
     - **Username**: `john_doe`
     - **Password**: `patient123`
3. **Webcam Permissions**:
   - When launching the **Finger Tapping**, **Tremor Detection**, or **Gait Analysis** modules, click **Allow** when prompted for camera access. MediaPipe Vision requires live video input to calculate landmark kinematics.

---

### Database Management (SQLite)

The project uses a localized SQLite database (`database.sqlite`) to log user sessions, logins, and patient vitals.

- **Initialize / Reset Database**:
  ```bash
  npm run init-db
  ```
- **Inspect Tables**:
  Open `database.sqlite` using [DB Browser for SQLite](https://sqlitebrowser.org/) to view:
  - `users`: User profiles, roles, and credentials.
  - `login_logs`: Timestamped audit trail of patient and clinician logins.
  - `patient_vitals`: Recorded biometric vitals (blood pressure, SpO2, heart rate, wellness score).

---

### Available NPM Scripts

| Command | Working Directory | Description |
| :--- | :--- | :--- |
| `npm run dev` | Root or `tremor/` | Launches the Vite frontend dev server at `http://localhost:5173` |
| `npm run server` | Root or `tremor/` | Starts the Express.js API server on port `5000` |
| `npm run init-db` | Root or `tremor/` | Creates and seeds default tables in `database.sqlite` |
| `npm run build` | Root or `tremor/` | Compiles production assets into the `dist/` directory |
| `npm run preview`| Root or `tremor/` | Previews the production build locally |

---

### Optional: System Architecture Diagram Generator
To generate the high-resolution system architecture diagrams for the IEEE paper:
```bash
python generate_architecture_diagram.py
```
*(Requires `matplotlib` and `numpy` installed).*
