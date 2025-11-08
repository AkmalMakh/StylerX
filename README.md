# StylerX - Complete Personal Style & Color Analysis Platform

<div align="center">

![React Native](https://img.shields.io/badge/React%20Native-0.81.5-blue.svg)
![Expo](https://img.shields.io/badge/Expo-54.0.22-black.svg)
![FastAPI](https://img.shields.io/badge/FastAPI-0.121+-green.svg)
![Python](https://img.shields.io/badge/Python-3.12+-blue.svg)

**AI-Powered Personal Color Analysis & Fashion Intelligence Platform**

[Frontend](#-frontend-react-native-mobile-app) • [Backend](#-backend-fastapi-server) • [Architecture](#-system-architecture) • [Quick Start](#-quick-start)

</div>

---

## 📱 Screenshots

<table>
  <tr>
    <td><strong>Before</strong></td>
    <td><strong>After</strong></td>
  </tr>
  <tr>
    <td><img src="./before.PNG" width="400" alt="Before" /></td>
    <td><img src="./after.PNG" width="400" alt="After" /></td>
  </tr>
</table>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [System Architecture](#-system-architecture)
- [Frontend (React Native Mobile App)](#-frontend-react-native-mobile-app)
- [Backend (FastAPI Server)](#-backend-fastapi-server)
- [Quick Start](#-quick-start)
- [API Documentation](#-api-documentation)
- [Development Guide](#-development-guide)
- [Troubleshooting](#-troubleshooting)

---

## 🎯 Overview

**StylerX** is a complete full-stack application that combines a React Native mobile app with a FastAPI backend to provide AI-powered personal color analysis and fashion recommendations. The platform uses ensemble learning with three state-of-the-art AI models (Gemini 2.5, GPT-4o, Claude 3.5) to analyze facial features, determine personal color seasons, and provide virtual try-on capabilities.

### How It Works

1. **User takes a photo** using the mobile app
2. **Frontend sends image** to the backend API (base64 encoded)
3. **Backend processes** using AI ensemble models
4. **Results are returned** with color season, confidence, and recommendations
5. **User saves results** to their profile and browses matching outfits
6. **Virtual try-on** allows users to see how outfits look before buying

---

## ✨ Features

### 🎨 Personal Color Analysis
- **Multi-Model AI Ensemble**: Uses Gemini, OpenAI GPT-4o, and Claude 3.5 simultaneously
- **12-Season Classification**: Scientific color analysis based on CIELAB colorimetry
- **High Accuracy**: 90%+ accuracy through ensemble learning
- **Confidence Scoring**: Transparent metrics for every analysis

### 👔 Virtual Try-On
- **Full Outfit Visualization**: See top + bottom + shoes together
- **Sequential Processing**: Realistic layering of clothing items
- **AI-Powered Generation**: High-quality try-on images

### 👕 Fashion Recommendations
- **Personalized Matching**: Outfits matched to your color season
- **Category Filtering**: Browse by type (t-shirts, trousers, jackets, etc.)
- **Popularity Ranking**: Discover trending items

### 👤 User Management
- **Secure Authentication**: JWT-based login system
- **Profile Management**: Save and track color analysis history
- **Wardrobe Collection**: Like and organize favorite items
- **Analysis History**: Review past analyses

### 📱 Mobile Experience
- **Cross-Platform**: iOS and Android support
- **Camera Integration**: Direct photo capture for analysis
- **Swipe Interface**: Tinder-like outfit discovery
- **Offline Support**: Cached data for better performance

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Mobile App (Frontend)                    │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │   Camera     │  │  Outfit Swipe │  │   Wardrobe   │      │
│  │   Profile    │  │     Screen    │  │   Screen     │      │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘      │
│         │                  │                  │              │
│         └──────────────────┼──────────────────┘              │
│                            │                                  │
│                    ┌───────▼────────┐                        │
│                    │  AuthContext   │                        │
│                    │  API Client    │                        │
│                    └───────┬────────┘                        │
└────────────────────────────┼─────────────────────────────────┘
                             │
                    HTTPS/REST API
                             │
┌────────────────────────────▼─────────────────────────────────┐
│              FastAPI Backend Server                           │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │  Auth Router │  │ Color Router │  │ Try-On Router│      │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘      │
│         │                  │                  │              │
│         └──────────────────┼──────────────────┘              │
│                            │                                  │
│  ┌─────────────────────────▼──────────────────────────┐    │
│  │         AI Ensemble Processing Engine                │    │
│  │  ┌────────┐  ┌────────┐  ┌────────┐                │    │
│  │  │ Gemini │  │ GPT-4o │  │ Claude │                │    │
│  │  │  2.5   │  │ Vision │  │  3.5   │                │    │
│  │  └───┬────┘  └───┬────┘  └───┬────┘                │    │
│  │      └───────────┼───────────┘                      │    │
│  │            Result Aggregation                        │    │
│  └───────────────────┬──────────────────────────────────┘    │
│                      │                                        │
│  ┌───────────────────▼──────────────────────────────────┐    │
│  │              Database Layer                           │    │
│  │  ┌──────────────┐  ┌──────────────┐                │    │
│  │  │  SQLite DB   │  │  Google Sheets│                │    │
│  │  │ (User Data)  │  │ (Fashion DB)  │                │    │
│  │  └──────────────┘  └──────────────┘                │    │
│  └──────────────────────────────────────────────────────┘    │
└──────────────────────────────────────────────────────────────┘
```

---

## 📱 Frontend (React Native Mobile App)

### Overview

The frontend is a React Native application built with Expo, providing a cross-platform mobile experience for iOS and Android. It uses file-based routing with Expo Router and TypeScript for type safety.

### Tech Stack

- **Expo** ~54.0.22 - Development platform
- **React Native** 0.81.5 - Mobile framework
- **React** 19.1.0 - UI library
- **Expo Router** - File-based navigation
- **TypeScript** - Type safety
- **Expo Camera** - Photo capture
- **Expo Image Picker** - Gallery access
- **AsyncStorage** - Local data persistence

### Project Structure

```
expo_project/
├── app/                      # Main app screens (file-based routing)
│   ├── (tabs)/              # Tab navigation screens
│   │   ├── outfit-swipe.tsx # Outfit discovery with swipe
│   │   ├── wardrobe.tsx     # Saved items & virtual try-on
│   │   └── profile.tsx      # User profile & color results
│   ├── onboarding/         # Onboarding flow
│   │   ├── preparation.tsx # Pre-analysis instructions
│   │   ├── camera-profile.tsx # Photo capture
│   │   └── analysis-progress.tsx # Progress screen
│   ├── analysis-results.tsx # Color analysis results
│   ├── login.tsx            # User login
│   └── signup.tsx           # User registration
├── components/              # Reusable UI components
├── contexts/               # React contexts
│   └── AuthContext.tsx     # Authentication state
├── utils/                  # Utility functions
└── assets/                 # Images and static assets
```

### Key Features

- **File-Based Routing**: Automatic route generation from file structure
- **Authentication Context**: Global auth state management
- **Camera Integration**: Direct photo capture for color analysis
- **Image Processing**: Base64 encoding for API communication
- **State Management**: React hooks and context API
- **Error Handling**: User-friendly error messages and retry logic

### Installation & Setup

```bash
# Navigate to frontend directory
cd expo_project

# Install dependencies
npm install

# Start development server
npm start

# Run on iOS
npm run ios

# Run on Android
npm run android

# Run on web
npm run web
```

### Configuration

The API base URL is configured in individual screen files:

```typescript
const API_BASE_URL = "https://stylist-ai-be.onrender.com";
```

For local development, update this to your local backend URL:

```typescript
const API_BASE_URL = "http://localhost:8000";
```

---

## 🖥️ Backend (FastAPI Server)

### Overview

The backend is a high-performance FastAPI server that handles AI-powered color analysis, user authentication, outfit recommendations, and virtual try-on generation. It uses ensemble learning with three AI models for maximum accuracy.

### Tech Stack

- **FastAPI** 0.121+ - Modern async web framework
- **Python** 3.12+ - Programming language
- **SQLAlchemy** - ORM for database management
- **Pydantic** - Data validation
- **JWT** - Authentication tokens
- **Uvicorn** - ASGI server

### AI Models

- **Google Gemini 2.5 Flash** - Fast, efficient vision analysis
- **OpenAI GPT-4o Vision** - Highest accuracy, deep analysis
- **Anthropic Claude 3.5 Sonnet** - Best reasoning and explanations

### Project Structure

```
StylerX/backend/stylist_ai_be/
├── app.py                  # Main FastAPI application
├── src/
│   ├── api/               # API route handlers
│   │   ├── auth.py        # Authentication endpoints
│   │   ├── color.py       # Color analysis endpoints
│   │   ├── try_on.py      # Virtual try-on endpoints
│   │   ├── outfits.py     # Outfit recommendations
│   │   └── user_*.py      # User management endpoints
│   ├── database/          # Database models and setup
│   ├── models/            # AI model integrations
│   └── utils/             # Utility functions
├── data/                  # Fashion item database
├── pyproject.toml         # Python dependencies
└── README.md             # Backend documentation
```

### Installation & Setup

```bash
# Navigate to backend directory
cd StylerX/backend/stylist_ai_be

# Install uv (Python package manager)
curl -LsSf https://astral.sh/uv/install.sh | sh

# Create .env file with API keys
cat > .env << EOF
GEMINI_API_KEY=your_gemini_key_here
OPENAI_API_KEY=your_openai_key_here
ANTHROPIC_API_KEY=your_anthropic_key_here
SECRET_KEY=your_jwt_secret_key_here
EOF

# Install dependencies
uv sync

# Run the server
uv run python3 app.py
```

The API will be available at `http://localhost:8000` with interactive docs at `http://localhost:8000/docs`.

### Environment Variables

Create a `.env` file in the backend directory:

```env
GEMINI_API_KEY=your_gemini_api_key
OPENAI_API_KEY=your_openai_api_key
ANTHROPIC_API_KEY=your_anthropic_api_key
SECRET_KEY=your_jwt_secret_key_here
```

---

## 🚀 Quick Start

### Prerequisites

**For Frontend:**
- Node.js v18+
- npm or yarn
- Expo CLI (or use npx)
- iOS Simulator (Mac) or Android Studio

**For Backend:**
- Python 3.12+
- API Keys: Google Gemini, OpenAI, Anthropic Claude
- uv package manager (optional but recommended)

### Step-by-Step Setup

#### 1. Clone the Repository

```bash
git clone <repository-url>
cd Styler
```

#### 2. Set Up Backend

```bash
# Navigate to backend
cd StylerX/backend/stylist_ai_be

# Install uv (if not installed)
curl -LsSf https://astral.sh/uv/install.sh | sh

# Create .env file with your API keys
cat > .env << EOF
GEMINI_API_KEY=your_key_here
OPENAI_API_KEY=your_key_here
ANTHROPIC_API_KEY=your_key_here
SECRET_KEY=your_secret_key
EOF

# Install dependencies
uv sync

# Start backend server
uv run python3 app.py
```

Backend will run on `http://localhost:8000`

#### 3. Set Up Frontend

```bash
# Navigate to frontend (in a new terminal)
cd expo_project

# Install dependencies
npm install

# Update API_BASE_URL in files if using local backend
# Change from: "https://stylist-ai-be.onrender.com"
# To: "http://localhost:8000"

# Start Expo development server
npm start
```

#### 4. Run the App

- Press `i` for iOS Simulator
- Press `a` for Android Emulator
- Scan QR code with Expo Go app
- Press `w` for web browser

---

## 📚 API Documentation

### Base URL

- **Production**: `https://stylist-ai-be.onrender.com`
- **Local Development**: `http://localhost:8000`

### Authentication

#### Register User

```http
POST /api/auth/register
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "secure_password"
}
```

**Response:**
```json
{
  "user_id": 1,
  "email": "user@example.com",
  "access_token": "eyJhbGciOiJIUzI1NiIs...",
  "token_type": "bearer"
}
```

#### Login

```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "secure_password"
}
```

### Color Analysis

#### Hybrid Ensemble Analysis (Recommended)

```http
POST /api/analyze/color/ensemble/hybrid?judge_model=openai
Content-Type: application/json

{
  "image": "data:image/png;base64,iVBORw0KGgo..."
}
```

**Query Parameters:**
- `judge_model`: `"gemini"`, `"openai"`, or `"claude"` (default: `"openai"`)

**Response:**
```json
{
  "personal_color_type": "Deep Autumn",
  "confidence": 0.92,
  "undertone": "warm",
  "season": "autumn",
  "subtype": "deep",
  "reasoning": "Analysis reasoning..."
}
```

#### Single Model Analysis (Faster)

```http
POST /api/analyze/color
Content-Type: application/json

{
  "image": "data:image/png;base64,..."
}
```

### User Profile & Color Results

#### Save Color Analysis

```http
POST /api/user/color/save
Authorization: Bearer <token>
Content-Type: application/json

{
  "personal_color_type": "Deep Autumn",
  "confidence": 0.92,
  "undertone": "warm",
  "season": "autumn",
  "subtype": "deep",
  "reasoning": "..."
}
```

#### Get User's Color Results

```http
GET /api/user/color/results?limit=1
Authorization: Bearer <token>
```

#### Get User Profile

```http
GET /api/user/profile
Authorization: Bearer <token>
```

### Outfits & Wardrobe

#### Get Outfits by Season

```http
GET /api/outfit/season/{season}
```

**Example:** `/api/outfit/season/autumn`

#### Like an Outfit

```http
POST /api/user/outfits/like
Authorization: Bearer <token>
Content-Type: application/json

{
  "item_id": "12345"
}
```

#### Get Liked Outfits

```http
GET /api/user/outfits/liked
Authorization: Bearer <token>
```

#### Unlike an Outfit

```http
DELETE /api/user/outfits/like/{item_id}
Authorization: Bearer <token>
```

### Virtual Try-On

#### Full Outfit Try-On (Sequential)

```http
POST /api/try-on/generate-full-outfit/on-sequential
Content-Type: application/json

{
  "user_image": "data:image/png;base64,...",
  "upper_image": "data:image/png;base64,...",
  "lower_image": "data:image/png;base64,...",
  "shoes_image": "data:image/png;base64,..."
}
```

**Response:**
```json
{
  "try_on_full_outfit_on_sequential_image": "data:image/png;base64,...",
  "status": "success",
  "message": "Outfit try-on on sequential image generated successfully"
}
```

#### Single Item Try-On

```http
POST /api/try-on/generate
Content-Type: application/json

{
  "user_image": "data:image/png;base64,...",
  "product_image": "data:image/png;base64,..."
}
```

### Complete API Endpoint Reference

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| `POST` | `/api/auth/register` | Register new user | No |
| `POST` | `/api/auth/login` | Login user | No |
| `POST` | `/api/analyze/color/ensemble/hybrid` | Hybrid ensemble color analysis | No |
| `POST` | `/api/analyze/color` | Single model color analysis | No |
| `GET` | `/api/user/profile` | Get user profile | Yes |
| `GET` | `/api/user/color/results` | Get color analysis history | Yes |
| `POST` | `/api/user/color/save` | Save color analysis | Yes |
| `GET` | `/api/outfit/season/{season}` | Get outfits by season | No |
| `GET` | `/api/user/outfits/liked` | Get liked outfits | Yes |
| `POST` | `/api/user/outfits/like` | Like an outfit | Yes |
| `DELETE` | `/api/user/outfits/like/{item_id}` | Unlike an outfit | Yes |
| `POST` | `/api/try-on/generate-full-outfit/on-sequential` | Full outfit try-on | No |
| `POST` | `/api/try-on/generate` | Single item try-on | No |

---

## 🛠️ Development Guide

### Frontend Development

#### Running in Development Mode

```bash
cd expo_project
npm start
```

#### Code Structure

- **Screens**: Located in `app/` directory, use file-based routing
- **Components**: Reusable components in `components/`
- **Contexts**: Global state in `contexts/`
- **Utils**: Helper functions in `utils/`

#### Key Patterns

- **Navigation**: Use `expo-router` for navigation
- **State**: Use React hooks (`useState`, `useEffect`) and Context API
- **API Calls**: Use `fetch` with proper error handling
- **Images**: Convert to base64 for API communication

### Backend Development

#### Running in Development Mode

```bash
cd StylerX/backend/stylist_ai_be
uv run python3 app.py
```

#### Code Structure

- **Routes**: API endpoints in `src/api/`
- **Models**: Database models in `src/database/`
- **AI Integration**: Model wrappers in `src/models/`
- **Utils**: Helper functions in `src/utils/`

#### Adding New Endpoints

1. Create route handler in `src/api/`
2. Add router to `app.py`
3. Update API documentation

### Testing

#### Frontend Testing

```bash
cd expo_project
npm run lint
```

#### Backend Testing

```bash
cd StylerX/backend/stylist_ai_be
uv run pytest  # If tests are set up
```

---

## 🔧 Troubleshooting

### Frontend Issues

#### iOS Build Problems

```bash
cd expo_project/ios
pod install
cd ..
npm run ios
```

#### Clear Cache

```bash
npx expo start --clear
```

#### Metro Bundler Issues

```bash
# Kill Metro bundler
killall node

# Restart
npm start
```

### Backend Issues

#### Port Already in Use

```bash
# Find process using port 8000
lsof -i :8000

# Kill the process
kill -9 <PID>
```

#### Missing Dependencies

```bash
cd StylerX/backend/stylist_ai_be
uv sync
```

#### API Key Errors

- Verify all API keys are set in `.env` file
- Check API key permissions and quotas
- Ensure keys are not expired

### Common Issues

#### CORS Errors

Backend CORS is configured to allow all origins. For production, update `app.py`:

```python
app.add_middleware(
    CORSMiddleware,
    allow_origins=["https://yourdomain.com"],  # Specific origins
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

#### Image Upload Failures

- Ensure images are properly base64 encoded
- Check image size limits
- Verify image format is supported (JPEG, PNG)

#### Authentication Issues

- Verify JWT token is included in headers
- Check token expiration
- Ensure `SECRET_KEY` matches between environments

---

## 📊 Performance Metrics

| Metric | Single Model | Parallel Ensemble | Hybrid Ensemble |
|--------|-------------|------------------|-----------------|
| Response Time | 2-4s | 3-8s | 5-12s |
| Accuracy | ~85% | ~90% | ~95% |
| Cost/Request | Low | Medium | High |
| Recommended Use | Quick checks | Production | Critical decisions |

---

## 🗺️ Project Roadmap

### Phase 1: Core Features ✅
- [x] Multi-model ensemble system
- [x] Color analysis with 12-season classification
- [x] User authentication and profiles
- [x] Fashion recommendations
- [x] Virtual try-on
- [x] Mobile app (iOS/Android)

### Phase 2: Enhanced UX
- [ ] Real-time analysis progress
- [ ] Color palette visualization
- [ ] Style comparison tools
- [ ] Push notifications

### Phase 3: Advanced Features
- [ ] Makeup and hair color recommendations
- [ ] Capsule wardrobe generator
- [ ] Social sharing and community
- [ ] AR virtual try-on
- [ ] Multi-language support

### Phase 4: Scale & Optimize
- [ ] Response caching
- [ ] Image quality validation
- [ ] Advanced analytics dashboard
- [ ] API rate limiting and quotas
- [ ] Database optimization

---

## 📄 License

This project is private and proprietary.

---

## 🙏 Acknowledgments

- Color science research based on CIELAB colorimetry standards
- 12-season analysis methodology from professional color consultants
- AI models provided by Google, OpenAI, and Anthropic
- Fashion data curated from leading retailers

---

## 📞 Support

For issues, questions, or contributions, please contact the development team.

---

<div align="center">

**Built with ❤️ for StylerX**

Made by Aki's Team

[⬆ Back to Top](#-stylerx---complete-personal-style--color-analysis-platform)

</div>

