# EmailForge Deployment Guide

## Deploy to Render

### Prerequisites
1. Push your code to GitHub repository
2. Create account at [render.com](https://render.com)

### Steps
1. Connect GitHub repository to Render
2. Create a new Web Service
3. Use these settings:
   - **Build Command**: `npm install && npm run build`
   - **Start Command**: `npm start`
   - **Environment**: Node
   - **Plan**: Free (or paid for better performance)

### Environment Variables
Add these in Render dashboard:
- `VITE_FIREBASE_API_KEY`: Your Firebase API key
- `VITE_FIREBASE_PROJECT_ID`: relaysai
- `VITE_FIREBASE_APP_ID`: Your Firebase App ID
- `GOOGLE_CLIENT_ID`: Your Google OAuth Client ID
- `GOOGLE_CLIENT_SECRET`: Your Google OAuth Client Secret
- `GROQ_API_KEY`: Your Groq API key
- `NODE_ENV`: production

### Firebase Configuration
After deploying to Render, add your Render domain to Firebase:

1. Go to Firebase Console → Authentication → Settings
2. Add your Render domain to "Authorized domains":
   - `your-app-name.onrender.com`
   - `your-app-name.render.com`

### Google OAuth Configuration
1. Go to Google Cloud Console → APIs & Credentials
2. Edit your OAuth 2.0 client
3. Add authorized redirect URIs:
   - `https://your-app-name.onrender.com/auth/gmail/callback`

## Deploy to Other Platforms

### Vercel
- Connect GitHub repo
- Add environment variables
- Deploy automatically

### Heroku
- Use `Dockerfile` for container deployment
- Add Heroku Postgres addon for database

### Railway
- Connect GitHub repo  
- Add environment variables
- Auto-deploy on push

## Post-Deployment
1. Test user authentication
2. Test Gmail OAuth connection
3. Verify email sending functionality
4. Monitor application logs

## Troubleshooting
- **Firebase auth error**: Check authorized domains
- **Gmail OAuth error**: Check redirect URIs in Google Console
- **Build errors**: Ensure all environment variables are set