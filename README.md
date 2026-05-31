# Sculpt - Appointment Scheduling App

This project consists of a React frontend and a Node.js backend for appointment scheduling with Google Calendar integration.

## Frontend

Built with React + Vite.

### Setup

1. Install dependencies:
   ```
   npm install
   ```

2. Copy environment variables:
   ```
   cp .env.example .env.local
   ```

3. Configure your environment variables (see Google Calendar API Setup below)

4. Start the development server:
   ```
   npm run dev
   ```

## Backend

Node.js Express API for managing appointments.

### Setup

1. Navigate to the backend directory:
   ```
   cd backend
   ```

2. Install dependencies:
   ```
   npm install
   ```

3. Start the server:
   ```
   npm start
   ```

The backend runs on http://localhost:5000

### API Endpoints

- `GET /api/appointments` - Get all appointments
- `POST /api/appointments` - Create new appointment
- `PUT /api/appointments/:id` - Update appointment
- `DELETE /api/appointments/:id` - Delete appointment

## Google Calendar API Setup

To enable Google Calendar integration:

### 1. Create a Google Cloud Project

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable the **Google Calendar API**

### 2. Create OAuth 2.0 Credentials

1. Go to "APIs & Services" > "Credentials"
2. Click "Create Credentials" > "OAuth 2.0 Client IDs"
3. Choose "Web application" as application type
4. **Add authorized JavaScript origins** (IMPORTANT):
   - `http://localhost:5178` (for development)
   - `http://localhost` (for port-agnostic local development)
   - Your production domain
5. **Add authorized redirect URIs**:
   - `http://localhost:5178` (for development)
   - `http://localhost` (for port-agnostic local development)
   - Your production domain
6. Click "Create" and copy your **Client ID**

### 3. Create API Key

1. Go to "APIs & Services" > "Credentials"
2. Click "Create Credentials" > "API key"
3. Copy your **API Key**

### 4. Configure Environment Variables

Add these to your `.env.local` file:

```env
VITE_GOOGLE_CLIENT_ID=your_client_id.apps.googleusercontent.com
VITE_GOOGLE_API_KEY=your_api_key
```

### 5. Troubleshooting redirect_uri_mismatch

If you get `redirect_uri_mismatch` error:

✅ **What to check:**
1. In Google Cloud Console, go to your OAuth 2.0 Client ID credentials
2. Under "Authorized JavaScript origins", add **both**:
   - `http://localhost:5178` (exact port)
   - `http://localhost` (without port, useful when port changes)
3. Under "Authorized redirect URIs", add the same
4. **Save changes**
5. Hard refresh your browser (Ctrl+F5 or Cmd+Shift+R)
6. Try connecting again

### 6. How It Works

- Click "Connect to Google Calendar" on `/appointments`
- Sign in with Google and approve permissions
- Token is saved in browser storage
- Click "Sync to Calendar" to add appointments



## Features

- Appointment scheduling and management
- Admin dashboard with appointment overview
- Google Calendar integration for appointment syncing
- Firebase backend for data persistence
- Responsive design

## Notes

- Backend currently uses in-memory storage
- Integrate with Firebase Firestore for persistent storage
