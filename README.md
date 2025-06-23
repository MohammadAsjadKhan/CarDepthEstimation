# 🚗 Car Headlight Depth Estimation System

A real-time web-based computer vision application that estimates the distance to objects illuminated by car headlights using live camera feed from your laptop.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [System Architecture](#system-architecture)
- [Installation & Setup](#installation--setup)
- [Usage Guide](#usage-guide)
- [Configuration](#configuration)
- [Technical Implementation](#technical-implementation)
- [Browser Compatibility](#browser-compatibility)
- [Limitations](#limitations)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Overview

This project addresses the challenge of real-time distance estimation for automotive safety applications. By mounting a laptop on a car's hood and analyzing the camera feed, the system identifies objects in the headlight beam path and estimates their distance from the vehicle.

**Primary Use Case**: Safety assistance for nighttime driving by providing real-time obstacle detection and distance measurement.

## ✨ Features

### Core Functionality
- 📹 **Real-time Camera Access**: Direct webcam integration using browser APIs
- 🔍 **Bright Region Detection**: Identifies areas illuminated by headlights
- 📏 **Distance Estimation**: Calculates approximate distance to nearest objects
- 🎯 **Center Region Analysis**: Focuses on the primary driving path
- ⚡ **Real-time Processing**: 30+ FPS performance with live visualization

### User Interface
- 🎨 **Modern Glassmorphism Design**: Professional, intuitive interface
- 📊 **Live Metrics Dashboard**: Real-time display of distance, FPS, and detection data
- ⚙️ **Adjustable Parameters**: Customizable detection sensitivity and thresholds
- 🚨 **Distance Alerts**: Visual warnings for objects closer than 5 meters
- 📸 **Frame Capture**: Save processed frames with overlay annotations

### Technical Features
- 📱 **Responsive Design**: Works on desktop and mobile devices
- 🔧 **Configurable Settings**: Real-time parameter adjustment
- 📈 **Performance Monitoring**: FPS counter and processing metrics
- 🎥 **Multi-camera Support**: Automatic fallback between front/rear cameras

## 🛠 Technology Stack

### Frontend Technologies
- **HTML5**: Structure and canvas rendering
- **CSS3**: Modern styling with glassmorphism effects
- **Vanilla JavaScript**: Real-time processing and camera handling
- **Canvas API**: Overlay rendering and image processing
- **MediaDevices API**: Camera access and stream handling

### Computer Vision Algorithms
- **Brightness-based Detection**: Identifies headlight-illuminated regions
- **Morphological Operations**: Noise reduction and region cleanup
- **Contour Analysis**: Shape detection and area filtering
- **Distance Calculation**: Depth estimation using geometric principles

## 🏗 System Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Browser UI    │    │   Camera Feed    │    │  Image Analysis │
│                 │◄──►│                  │◄──►│                 │
│ • Controls      │    │ • Live Stream    │    │ • Bright Detect │
│ • Metrics       │    │ • Frame Capture  │    │ • Distance Calc │
│ • Alerts        │    │ • Resolution     │    │ • Overlay Draw  │
└─────────────────┘    └──────────────────┘    └─────────────────┘
         ▲                       ▲                       ▲
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
                    ┌──────────────────┐
                    │  Settings Panel  │
                    │                  │
                    │ • Thresholds     │
                    │ • Sensitivity    │
                    │ • Display Options│
                    └──────────────────┘
```

## 🚀 Installation & Setup

### Prerequisites
- Modern web browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- Laptop with built-in camera or external webcam
- HTTPS connection (required for camera access)

### Quick Start

1. **Download the Project**
   ```bash
   # Clone the repository
   git clone https://github.com/your-username/headlight-depth-estimation.git
   cd headlight-depth-estimation
   ```

2. **Run Locally**
   ```bash
   # Option 1: Simple HTTP server (Python)
   python -m http.server 8000
   
   # Option 2: Node.js server
   npx http-server
   
   # Option 3: PHP server
   php -S localhost:8000
   ```

3. **Access the Application**
   - Open browser and navigate to `https://localhost:8000`
   - Or simply open the `index.html` file directly in your browser

### Production Deployment

For production deployment, ensure HTTPS is enabled as browsers require secure connections for camera access.

## 📖 Usage Guide

### Initial Setup

1. **Launch Application**
   - Open the HTML file in a supported browser
   - Ensure camera permissions are enabled

2. **Start Camera**
   - Click the "Start Camera" button
   - Grant camera access when prompted
   - Wait for the video feed to initialize

3. **Position Setup**
   - Mount your laptop on the car's hood
   - Ensure headlights are visible in the camera frame
   - Adjust camera angle for optimal coverage

### Operation

1. **Real-time Monitoring**
   - Monitor the distance metrics panel
   - Observe bright region detection overlays
   - Watch for distance alerts

2. **Parameter Adjustment**
   - Adjust brightness threshold for different lighting conditions
   - Modify minimum area to filter noise
   - Scale depth sensitivity based on environment

3. **Data Capture**
   - Use "Capture Frame" to save important moments
   - Monitor FPS for performance optimization

### Controls Reference

| Control | Function |
|---------|----------|
| **Start Camera** | Initialize webcam and begin processing |
| **Stop Camera** | Stop camera feed and processing |
| **Capture Frame** | Save current frame with overlays |
| **Brightness Threshold** | Adjust sensitivity to bright areas (100-255) |
| **Min Area** | Set minimum size for valid regions (100-2000px) |
| **Depth Scale** | Adjust distance calculation factor (1-50) |
| **Show Overlay** | Toggle visualization overlays on/off |

## ⚙️ Configuration

### Detection Parameters

```javascript
// Default configuration
const defaultSettings = {
    brightnessThreshold: 180,  // Brightness cutoff for headlight detection
    minArea: 500,              // Minimum pixel area for valid regions  
    depthScale: 10,            // Distance calculation scaling factor
    showOverlay: true,         // Display visual overlays
    alertDistance: 5           // Distance threshold for warnings (meters)
};
```

### Camera Settings

```javascript
// Camera constraints
const cameraConfig = {
    video: {
        width: { ideal: 1280, min: 640 },
        height: { ideal: 720, min: 480 },
        frameRate: { ideal: 30, min: 15 },
        facingMode: 'environment' // Prefer rear camera
    }
};
```

## 🔧 Technical Implementation

### Core Components

#### 1. Camera Management
```javascript
class CameraManager {
    // Handles camera initialization, stream management, and error handling
    // Supports multiple camera types with automatic fallback
}
```

#### 2. Image Processing
```javascript
class ImageProcessor {
    // Implements bright region detection
    // Performs morphological operations
    // Calculates region properties
}
```

#### 3. Depth Estimation
```javascript
class DepthEstimator {
    // Simulates depth calculation (ready for ML model integration)
    // Provides distance metrics and analysis
}
```

#### 4. Visualization Engine
```javascript
class VisualizationEngine {
    // Renders overlay graphics
    // Manages canvas operations
    // Updates UI metrics
}
```

### Algorithm Flow

1. **Frame Capture**: Acquire video frame from camera stream
2. **Preprocessing**: Convert to grayscale and apply noise reduction
3. **Bright Detection**: Threshold-based identification of illuminated areas
4. **Region Analysis**: Filter regions by size and calculate properties
5. **Distance Estimation**: Apply geometric calculations for depth
6. **Visualization**: Render overlays and update metrics
7. **Alert Processing**: Check thresholds and trigger warnings

## 🌐 Browser Compatibility

| Browser | Version | Support Level |
|---------|---------|---------------|
| **Chrome** | 90+ | ✅ Full Support |
| **Firefox** | 88+ | ✅ Full Support |
| **Safari** | 14+ | ✅ Full Support |
| **Edge** | 90+ | ✅ Full Support |
| **Opera** | 76+ | ✅ Full Support |
| **Mobile Chrome** | 90+ | ✅ Full Support |
| **Mobile Safari** | 14+ | ✅ Full Support |

### Required APIs
- MediaDevices.getUserMedia()
- Canvas 2D Context
- RequestAnimationFrame
- Blob and URL APIs

## ⚠️ Limitations

### Current Implementation
- **Simulated depth estimation**: Uses geometric approximation rather than ML models
- **Lighting dependency**: Requires adequate ambient light and headlight illumination
- **Single camera**: Monocular depth estimation has inherent accuracy limitations
- **Browser-only processing**: Limited computational resources compared to native applications

### Environmental Constraints
- Performance varies with lighting conditions
- Accuracy affected by weather (rain, fog, snow)
- Limited effective range (typically 2-20 meters)
- Requires stable camera mounting

### Technical Limitations
- No persistent storage of calibration data
- Limited to browser security constraints
- Dependent on camera quality and specifications

## 🚀 Future Enhancements

### Phase 1: Core Improvements
- [ ] **ML Model Integration**: Implement MiDaS or similar depth estimation models
- [ ] **Backend Processing**: Add Python/Node.js server for heavy computations
- [ ] **Calibration System**: Camera calibration for improved accuracy
- [ ] **Data Persistence**: Save settings and calibration data

### Phase 2: Advanced Features
- [ ] **Stereo Vision**: Dual camera setup for improved depth accuracy
- [ ] **Object Classification**: Identify specific object types (vehicles, pedestrians)
- [ ] **Night Vision Enhancement**: IR camera support and low-light optimization
- [ ] **GPS Integration**: Location-aware processing and logging

### Phase 3: Production Features
- [ ] **Mobile App**: Native iOS/Android applications
- [ ] **Cloud Processing**: Serverless backend for model inference
- [ ] **Fleet Integration**: Multi-vehicle monitoring dashboard
- [ ] **Analytics Dashboard**: Historical data analysis and reporting

### Proposed Architecture Evolution

```
Current: Browser-only Processing
Future: Hybrid Browser + Server Architecture

┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Browser   │◄──►│   Server    │◄──►│  ML Models  │
│             │    │             │    │             │
│ • UI/UX     │    │ • Processing│    │ • MiDaS     │
│ • Camera    │    │ • WebSocket │    │ • YOLO      │
│ • Display   │    │ • Database  │    │ • Custom    │
└─────────────┘    └─────────────┘    └─────────────┘
```

## 🤝 Contributing

We welcome contributions! Please see our contributing guidelines:

### Development Setup
```bash
# Fork the repository
git fork https://github.com/your-username/headlight-depth-estimation

# Create feature branch
git checkout -b feature/your-feature-name

# Make changes and test
npm test  # or your testing command

# Submit pull request
git push origin feature/your-feature-name
```

### Contribution Areas
- 🐛 Bug fixes and performance improvements
- 🎨 UI/UX enhancements
- 🧠 Algorithm improvements
- 📚 Documentation and examples
- 🧪 Testing and validation

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Support & Contact

- **Issues**: [GitHub Issues](https://github.com/your-username/headlight-depth-estimation/issues)
- **Discussions**: [GitHub Discussions](https://github.com/your-username/headlight-depth-estimation/discussions)
- **Email**: your-email@example.com

---

**⚠️ Safety Notice**: This system is designed for research and development purposes. Do not rely solely on this system for critical safety decisions while driving. Always maintain proper attention and follow traffic safety regulations.
