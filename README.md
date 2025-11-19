---
title: VigilCam - AI Exam Proctoring System
colorFrom: blue
colorTo: cyan
sdk: docker
pinned: false
license: mit
app_port: 7860
---

# VigilCam - AI-Powered Exam Proctoring System

[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=flat-square&logo=node.js)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?style=flat-square&logo=mongodb)](https://www.mongodb.com/)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-Face_Mesh-00D9FF?style=flat-square)](https://google.github.io/mediapipe/)

Professional-grade, AI-powered exam proctoring system with real-time behavioral detection using browser-based machine learning.

## Features

- **Face Detection & Tracking**: Multi-face detection with 468 facial landmarks
- **Gaze Tracking**: Real-time iris position monitoring with calibration
- **Blink Detection**: Eye Aspect Ratio (EAR) calculation for accurate analysis
- **Behavioral Analysis**: Comprehensive violation detection with risk scoring
- **Browser-Based ML**: Client-side processing using MediaPipe (no server-side video processing)
- **Real-Time Monitoring**: WebSocket-based low-latency communication
- **Secure Authentication**: Passport.js with local and Google OAuth strategies
- **Comprehensive Reporting**: Downloadable JSON reports with detailed analytics

## Live Demo

Try it now: Click "App" above to access the live demo!

**Test Account:**
- Email: `demo@vigilcam.com`
- Password: `demo123`

Or create your own account to get started.

## How to Use

1. **Register/Login**: Create an account or sign in with Google
2. **Start Monitoring**: Click "START MONITORING" button
3. **Grant Permissions**: Allow camera access when prompted
4. **Calibration**: Look straight at camera for 3 seconds
5. **Monitoring Session**: The system will detect:
   - Multiple faces
   - Looking away from screen
   - Eyes closed for extended periods
   - Excessive blinking
   - Talking/mouth movement
   - Head turning away
6. **Stop & Report**: Click "STOP MONITORING" to generate detailed report

## Technology Stack

### Frontend
- Vanilla JavaScript
- MediaPipe Face Mesh (v0.4)
- Socket.IO Client
- EJS Templating

### Backend
- Node.js + Express.js
- Socket.IO Server
- Passport.js Authentication
- MongoDB (Atlas)

### ML Detection
- MediaPipe Face Mesh (468 landmarks)
- Browser-based Processing
- Real-time Frame Analysis

## Privacy & Security

- **No Video Recording**: All processing happens in your browser
- **No Data Storage**: Only detection statistics are saved
- **Secure Authentication**: bcrypt password hashing
- **Session Management**: Secure cookie-based sessions

## Detection Capabilities

| Detection Type | Description | Severity |
|---------------|-------------|----------|
| Multiple Faces | More than one person detected | HIGH |
| No Face | Candidate left frame | HIGH |
| Gaze Away | Looking away >4 seconds | MEDIUM |
| Eyes Closed | Eyes closed >4 seconds | MEDIUM |
| Excessive Blinking | >40 blinks per minute | MEDIUM |
| Head Turned | Significant head rotation | MEDIUM |
| Talking Detected | Mouth movement patterns | HIGH |

## Risk Score System

- **LOW RISK (0-24)**: Minimal suspicious activity
- **MODERATE RISK (25-49)**: Some concerns detected
- **HIGH RISK (50+)**: Significant violations detected

**Scoring Algorithm:**
- HIGH severity: +10 points
- MEDIUM severity: +5 points
- LOW severity: +2 points

## Configuration

Detection thresholds can be adjusted in `public/js/ml-detector.js`:

```javascript
THRESHOLDS = {
  EAR_BLINK: 0.21,              // Eye aspect ratio for blink detection
  EYES_CLOSED_TIME: 4000,       // Maximum eyes closed duration (ms)
  GAZE_AWAY_TIME: 4000,         // Maximum gaze away duration (ms)
  NO_FACE_TIME: 6000,           // Maximum time without face (ms)
  GAZE_X_DELTA: 0.07,           // Horizontal gaze tolerance
  GAZE_Y_DELTA: 0.06,           // Vertical gaze tolerance
  EXCESSIVE_BLINKS: 40,         // Blinks per minute threshold
  HEAD_TURN_THRESHOLD: 0.22     // Head turn detection threshold
}
```

## Browser Compatibility

- ✅ Chrome/Edge (Recommended)
- ✅ Firefox
- ✅ Safari
- ⚠️ Requires camera permissions

## Author

**Azhaan Ali Siddiqui**

- GitHub: [@AzhaanGlitch](https://github.com/AzhaanGlitch)
- LinkedIn: [Azhaan Ali Siddiqui](https://www.linkedin.com/in/azhaanalisiddiqui/)
- Email: azhaanalisiddiqui15@gmail.com

## License

This project is licensed under the MIT License.

## Acknowledgments

- [MediaPipe](https://google.github.io/mediapipe/) - Face mesh detection
- [Express.js](https://expressjs.com/) - Web framework
- [Socket.IO](https://socket.io/) - Real-time communication
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) - Database platform

## Issues & Feedback

Found a bug or have a suggestion? Please open an issue on [GitHub](https://github.com/AzhaanGlitch/VigilCam/issues).

---

**⭐ If you find this project useful, please consider giving it a star!**