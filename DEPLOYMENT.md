# 🚀 Free Deployment Options for SecureShare

## 1. **PythonAnywhere** (Recommended for Beginners)

### Steps:
1. **Create Account**: Go to [pythonanywhere.com](https://www.pythonanywhere.com) and sign up for free tier
2. **Create Web App**: 
   - Dashboard → Web → Add a new web app
   - Choose Flask framework
   - Python 3.9+ version
3. **Upload Code**:
   ```bash
   # Use PythonAnywhere console or git
   git clone <your-repo>
   # or upload files via web interface
   ```
4. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
5. **Configure WSGI**:
   ```python
   # In /var/www/<username>_pythonanywhere_com_wsgi.py
   import sys
   sys.path.append('/home/<username>/secure-file-sharing')
   from app import app as application
   ```
6. **Set Working Directory**: `/home/<username>/secure-file-sharing`

**Limitations**: 
- 1 web app, 2 background tasks
- 512MB storage
- Limited bandwidth

---

## 2. **Render** (Modern & Easy)

### Steps:
1. **Create Account**: [render.com](https://render.com)
2. **Push to GitHub**: 
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/username/secure-share.git
   git push -u origin main
   ```
3. **Deploy on Render**:
   - Dashboard → New → Web Service
   - Connect GitHub repository
   - Build Command: `pip install -r requirements.txt`
   - Start Command: `python app.py`
   - Port: 5000

**Free Tier**:
- 750 hours/month
- 512MB RAM
- Shared CPU

---

## 3. **Replit** (Easiest for Testing)

### Steps:
1. **Create Repl**: [replit.com](https://replit.com)
2. **Choose Python Template**
3. **Upload Files**: Drag & drop all project files
4. **Install Dependencies**: Shell tab → `pip install -r requirements.txt`
5. **Run**: Click "Run" button

**Limitations**:
- Always-on requires paid plan
- Limited storage
- Temporary URLs

---

## 4. **Vercel** (Static + Serverless)

### Steps:
1. **Install Vercel CLI**:
   ```bash
   npm i -g vercel
   ```
2. **Configure for Serverless**:
   ```python
   # vercel.json
   {
     "version": 2,
     "builds": [
       {
         "src": "app.py",
         "use": "@vercel/python"
       }
     ],
     "routes": [
       {
         "src": "/(.*)",
         "dest": "app.py"
       }
     ]
   }
   ```
3. **Deploy**:
   ```bash
   vercel --prod
   ```

**Limitations**: Need to adapt Flask for serverless functions

---

## 5. **Glitch** (Quick & Collaborative)

### Steps:
1. **Create Project**: [glitch.com](https://glitch.com)
2. **Choose Flask Starter**
3. **Replace Files**: Upload your project files
4. **Install Dependencies**: In package.json add requirements
5. **Auto-deploys** on save

**Limitations**: 
- Projects sleep after 5 minutes
- Limited resources

---

## 6. **Heroku** (Classic Option)

### Steps:
1. **Install Heroku CLI**
2. **Prepare App**:
   ```python
   # Procfile
   web: python app.py
   ```
3. **Deploy**:
   ```bash
   heroku create your-app-name
   git push heroku main
   heroku open
   ```

**Note**: Heroku no longer has free tier, but has cheap paid options

---

## 7. **Self-Hosted (Home Server)**

### Requirements:
- Old computer or Raspberry Pi
- Static IP or DDNS service
- Port forwarding

### Steps:
1. **Setup Server**:
   ```bash
   # Install Ubuntu/Debian
   sudo apt update
   sudo apt install python3 python3-pip nginx
   ```
2. **Configure App**:
   ```bash
   git clone <your-repo>
   cd secure-file-sharing
   pip3 install -r requirements.txt
   ```
3. **Setup Nginx**:
   ```nginx
   server {
       listen 80;
       server_name your-domain.com;
       location / {
           proxy_pass http://localhost:5000;
       }
   }
   ```
4. **Run with Gunicorn**:
   ```bash
   pip install gunicorn
   gunicorn -w 4 -b 0.0.0.0:5000 app:app
   ```

---

## 🛠️ Production Checklist

### Security:
- [ ] Use HTTPS (SSL certificates)
- [ ] Set up firewall
- [ ] Use environment variables for secrets
- [ ] Regular backups
- [ ] Monitor logs

### Performance:
- [ ] Use production database (PostgreSQL)
- [ ] Implement file cleanup
- [ ] Add rate limiting
- [ ] Use CDN for static files

### Database Setup:
```python
# For PostgreSQL
app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://user:pass@localhost/dbname'
```

### Environment Variables:
```bash
# .env file
SECRET_KEY=your-secret-key
DATABASE_URL=postgresql://...
UPLOAD_FOLDER=/path/to/uploads
```

---

## 🏆 **Recommended for You:**

**For Testing**: Use **Replit** or **Glitch**
**For Production**: Use **Render** (easiest) or **PythonAnywhere** (most stable)
**For Learning**: Use **Self-Hosted** on Raspberry Pi

---

## 📱 Quick Deploy with Render (Fastest):

1. Push code to GitHub
2. Go to render.com
3. Click "New Web Service"
4. Connect your GitHub repo
5. Use these settings:
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `python app.py`
   - **Port**: 5000
6. Click "Create Web Service"

Your app will be live at `https://your-app-name.onrender.com`

---

## ⚠️ Important Notes:

1. **File Storage**: Free tiers have limited storage
2. **Database**: SQLite works for testing, use PostgreSQL for production
3. **Domain**: Get free domain from Freenom (.tk, .ml, .ga)
4. **SSL**: Most platforms provide free SSL certificates
5. **Backups**: Regularly backup your database and files

Choose the option that best fits your needs and technical skill level!
