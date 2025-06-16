# 🚀 Quick Deploy Guide - Backend to Render

## Step 1: Deploy Backend di Render

### 1.1 Buka Render Dashboard
- Go to: https://dashboard.render.com/
- Login dengan GitHub account

### 1.2 Create New Web Service
- Click **"New +"** → **"Web Service"**
- Connect GitHub: `lillysummer01/OpenHands-Backend`
- Branch: `main`

### 1.3 Service Configuration
```
Name: openhands-novel-backend
Environment: Python
Region: Singapore (closest to Indonesia)
```

### 1.4 Build & Start Commands
```bash
# Build Command
pip install -r requirements.txt

# Start Command
python -m openhands.server.listen --host 0.0.0.0 --port $PORT
```

### 1.5 Environment Variables (REQUIRED)
Set these 3 variables in Render:

```bash
OPENROUTER_API_KEY=or-your-actual-openrouter-key-here
LLM_API_KEY=or-your-actual-openrouter-key-here  
SESSION_API_KEY=any-random-string-here
```

**Generate SESSION_API_KEY:**
```bash
# Use any random string, example:
SESSION_API_KEY=novel-writing-session-2024-secure-key
```

### 1.6 Deploy
- Click **"Create Web Service"**
- Wait 5-10 minutes for deployment
- Note your backend URL: `https://your-service-name.onrender.com`

## Step 2: Update Frontend Environment Variables

### 2.1 Di Vercel Dashboard
- Go to your frontend project
- Settings → Environment Variables
- Add/Update:

```bash
VITE_BACKEND_HOST=https://your-service-name.onrender.com
VITE_USE_TLS=true
VITE_FRONTEND_PORT=3001
VITE_INSECURE_SKIP_VERIFY=false
```

### 2.2 Redeploy Frontend
- Trigger new deployment di Vercel
- Frontend akan connect ke backend yang baru

## Step 3: Test Integration

### 3.1 Test Backend Health
```bash
curl https://your-service-name.onrender.com/api/health
```

### 3.2 Test Frontend Connection
- Open frontend URL
- Try Novel Writing Mode
- Check browser console for errors

## 🔑 OpenRouter API Key

### Get Your API Key:
1. Go to: https://openrouter.ai/
2. Sign up/Login
3. Go to **Keys** section
4. Create new key
5. Copy key (starts with `or-`)

### Add Balance:
1. Go to **Credits** section
2. Add minimum $5-10 for testing
3. Monitor usage in dashboard

## 🎯 Final URLs

After deployment:
- **Backend**: `https://your-backend-name.onrender.com`
- **Frontend**: `https://your-frontend-name.vercel.app`
- **Novel Writing Mode**: Frontend → Backend via WebSocket

## 🆘 Troubleshooting

### Backend Issues:
- Check Render logs for errors
- Verify OpenRouter API key is valid
- Ensure all 3 environment variables are set

### Frontend Issues:
- Check Vercel environment variables
- Verify backend URL is correct
- Check browser console for CORS errors

### Connection Issues:
- Test backend health endpoint
- Check CORS settings
- Verify WebSocket connection

---

**Deploy backend dulu, baru frontend bisa connect! 🎯**