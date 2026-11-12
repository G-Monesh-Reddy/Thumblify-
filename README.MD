# Thumblify – AI-Powered Thumbnail Generator

<p align="center">
  **Turn your ideas into eye-catching thumbnails with AI.**
</p>

<p align="center">
  A full-stack AI-powered thumbnail creation platform featuring intelligent prompt optimization, image generation, thumbnail recreation, and a creator community.
</p>

---

## Overview

**Thumblify** is a full-stack MERN application designed to help content creators generate visually engaging YouTube thumbnails quickly and efficiently.

It combines Groq-powered prompt optimization with Pollinations AI image generation to transform simple ideas into detailed thumbnail concepts.

Users can generate new thumbnails, recreate existing designs with targeted modifications, save their creations, and explore thumbnails shared by the community.

## Key Features

- **AI-Powered Prompt Optimization:** Uses Groq LLMs to transform simple user inputs into detailed, thumbnail-focused image prompts.
- **Thumbnail Generation:** Generate thumbnails using topics, styles, color palettes, aspect ratios, and optional custom prompts.
- **Thumbnail Recreation:** Provide an existing image URL and describe the modifications you want.
- **User Authentication:** Secure signup and login using JWT authentication and bcrypt password hashing.
- **Credit System:** Every new user receives 15 credits. One credit is deducted per successful generation.
- **Personal Thumbnail Library:** Save, view, and delete previously generated thumbnails.
- **Community Gallery:** Explore public thumbnails and discover trending creative ideas.
- **Like Functionality:** Engage with thumbnails shared by other creators.
- **Image Downloads:** Download generated thumbnails directly to your device.
- **Persistent Storage:** Store user information and thumbnail metadata using MongoDB.
- **Responsive Interface:** React-based interface designed for desktop and mobile screens.

## Application Workflow

```text
                 User
                  |
                  v
           Sign Up / Login
                  |
                  v
          JWT Authentication
                  |
                  v
           Thumbnail Studio
                  |
           +------+------+
           |             |
           v             v
      Generate Mode  Recreate Mode
           |             |
           v             v
       User Prompt    Image URL +
                      Change Request
           |             |
           +------+------+
                  |
                  v
        Groq Prompt Optimization
                  |
                  v
         Pollinations AI API
                  |
                  v
         Thumbnail Generation
                  |
                  v
          MongoDB Storage
                  |
                  v
           Credit Deduction
                  |
           +------+------+ 
           |      |       |
           v      v       v
          My   Community Download
      Generations Gallery
```

## Tech Stack

### Frontend

| Technology | Purpose |
|---|---|
| React 18 | UI development |
| Vite | Development and build tool |
| Tailwind CSS | Styling |
| React Router v6 | Client-side navigation |
| Context API | Authentication state management |
| JavaScript | Application logic |

### Backend

| Technology | Purpose |
|---|---|
| Node.js | JavaScript runtime |
| Express.js | REST API framework |
| MongoDB | Database |
| Mongoose | Database object modeling |
| JWT | Authentication |
| bcryptjs | Password hashing |
| Groq SDK | AI prompt optimization |
| dotenv | Environment configuration |
| CORS | Cross-origin resource sharing |
| Morgan | HTTP request logging |

### AI Services

| Service | Purpose |
|---|---|
| Groq API | LLM-powered prompt optimization |
| Pollinations AI | AI image generation |

## Project Structure

```text
Thumblify/
│
├── client/
│   ├── public/
│   ├── src/
│   │   ├── api/
│   │   ├── components/
│   │   ├── context/
│   │   ├── layouts/
│   │   ├── pages/
│   │   ├── utils/
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   ├── .env.example
│   ├── package.json
│   └── vite.config.js
│
├── server/
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── utils/
│   ├── .env.example
│   ├── package.json
│   └── server.js
│
├── .gitignore
└── README.md
```

## Getting Started

Follow these instructions to run Thumblify locally.

### Prerequisites

Make sure you have installed:

- Node.js (v18 or later)
- npm
- Git
- MongoDB Atlas account
- Groq API key
- Pollinations API key (if required by your selected Pollinations API access)

### 1. Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd Thumblify
```

### 2. Backend Setup

Navigate to the server directory:

```bash
cd server
npm install
```

Create a `.env` file inside the `server` directory.

**server/.env**

```env
PORT=5000

# Database
MONGO_URI=your_mongodb_connection_string

# Authentication
JWT_SECRET=your_strong_jwt_secret

# Groq AI
GROQ_API_KEY=your_groq_api_key
GROQ_MODEL=llama-3.3-70b-versatile

# Pollinations AI
POLLINATIONS_API_KEY=your_pollinations_api_key

# Frontend CORS
CLIENT_URL=http://localhost:5173
```

Start the backend development server:

```bash
npm run dev
```

If your project does not have a development script:

```bash
node server.js
```

Backend URL:

```text
http://localhost:5000
```

### 3. Frontend Setup

Open another terminal and navigate to the client directory:

```bash
cd client
npm install
```

Create a `.env` file inside the `client` directory.

**client/.env**

```env
VITE_API_URL=http://localhost:5000/api
```

Start the frontend development server:

```bash
npm run dev
```

Frontend URL:

```text
http://localhost:5173
```

## Environment Variables

### Backend Environment Variables

| Variable | Description |
|---|---|
| `PORT` | Backend server port |
| `MONGO_URI` | MongoDB connection string |
| `JWT_SECRET` | Secret used to sign JWT tokens |
| `GROQ_API_KEY` | Groq API authentication key |
| `GROQ_MODEL` | Groq model used for prompt optimization |
| `POLLINATIONS_API_KEY` | API key for Pollinations AI image generation |
| `CLIENT_URL` | Frontend URL allowed by CORS |

### Frontend Environment Variables

| Variable | Description |
|---|---|
| `VITE_API_URL` | Backend API base URL |

**Security Guidelines**

- Never commit `.env` files to GitHub.
- Never expose Groq or Pollinations API keys in frontend code.
- Keep API keys and database credentials on the backend.
- Use strong, unique JWT secrets.
- Configure environment variables separately for local development and production.

## API Documentation

All API endpoints are prefixed with `/api`.

### Authentication APIs

| Method | Endpoint | Description |
|---|---|---|
| POST | `/auth/signup` | Register a new user |
| POST | `/auth/login` | Authenticate an existing user |
| GET | `/auth/me` | Retrieve authenticated user profile |

### AI Generation APIs

| Method | Endpoint | Description |
|---|---|---|
| POST | `/ai/generate-thumbnail` | Generate or recreate a thumbnail |

### Thumbnail Management APIs

| Method | Endpoint | Description |
|---|---|---|
| GET | `/thumbnails` | Get personal thumbnails |
| DELETE | `/thumbnails/:id` | Delete a thumbnail |
| GET | `/thumbnails/community` | Retrieve community thumbnails |
| POST | `/thumbnails/community/:id/like` | Like a community thumbnail |
| GET | `/thumbnails/proxy` | Proxy supported remote images |

### Health Check

| Method | Endpoint | Description |
|---|---|---|
| GET | `/health` | Check backend availability |

### Authentication Header

Protected endpoints require a valid JWT token.

```http
Authorization: Bearer YOUR_JWT_TOKEN
```

## Deployment

Thumblify can be deployed using the following services:

| Component | Platform |
|---|---|
| Frontend | Vercel |
| Backend | Render |
| Database | MongoDB Atlas |
| Prompt Optimization | Groq API |
| Image Generation | Pollinations AI |

### Frontend Deployment – Vercel

1. Push the project to GitHub.
2. Import the repository into Vercel.
3. Set the root directory to `client`.
4. Select Vite as the framework preset.
5. Set the build command to `npm run build`.
6. Set the output directory to `dist`.
7. Add the following environment variable:

```env
VITE_API_URL=https://YOUR_BACKEND_URL/api
```

8. Deploy the application.

### Backend Deployment – Render

1. Open Render and create a new Web Service.
2. Connect your GitHub repository.
3. Set the root directory to `server`.
4. Set the build command:

```bash
npm install
```

5. Set the start command according to your package scripts:

```bash
npm start
```

Or:

```bash
node server.js
```

6. Add the backend environment variables:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_strong_jwt_secret

GROQ_API_KEY=your_groq_api_key
GROQ_MODEL=llama-3.3-70b-versatile

POLLINATIONS_API_KEY=your_pollinations_api_key

CLIENT_URL=https://YOUR_FRONTEND_URL
```

Render provides the `PORT` environment variable automatically. Your Express application should listen on `process.env.PORT || 5000` and bind to `0.0.0.0`.

7. Deploy the backend.
8. Update the frontend's `VITE_API_URL` with the deployed backend URL.

### MongoDB Atlas Configuration

1. Create or select a MongoDB Atlas cluster.
2. Configure database access credentials.
3. Configure network access to allow connections from your backend hosting environment.
4. Add the MongoDB connection string to the backend environment variables.

**Important:** Avoid unnecessarily exposing your database to all IP addresses. Use restricted network access where possible.

## Production Testing Checklist

After deployment, verify the following:

- [ ] Landing page loads successfully.
- [ ] User signup works.
- [ ] User login works.
- [ ] JWT authentication works.
- [ ] Profile restoration works after refresh.
- [ ] Thumbnail generation works.
- [ ] Thumbnail recreation works.
- [ ] Credits decrease after successful generation.
- [ ] My Generations displays saved thumbnails.
- [ ] Thumbnail deletion works.
- [ ] Community feed loads correctly.
- [ ] Like functionality works.
- [ ] Thumbnail downloads work.
- [ ] No CORS or API errors occur.

## Future Enhancements

- Multiple AI image-generation providers.
- Advanced image editing and customization.
- Text overlays and typography controls.
- Custom image uploads for recreation.
- Cloud image storage and optimization.
- Social sharing and creator profiles.
- Advanced analytics for thumbnail engagement.
- Subscription-based credit packages.

## Learning Outcomes

This project demonstrates practical implementation of:

- Full-stack MERN application development.
- REST API design and integration.
- JWT-based authentication and authorization.
- LLM integration and prompt engineering.
- AI-powered image-generation workflows.
- MongoDB schema design and CRUD operations.
- Frontend and backend deployment.
- Environment management and API security.

## License

This project is intended for educational and portfolio purposes. Add an appropriate open-source license if you intend to distribute or reuse it publicly.

---

<p align="center">
  **Built with ❤️ for content creators**
</p>

<p align="center">
  Thumblify – Create. Customize. Inspire.
</p>
