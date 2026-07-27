# KCS Service Marketplace - Complete Setup Guide

## 📋 Prerequisites

### System Requirements
- **Node.js**: Version 18.0.0 or higher
- **npm**: Version 9.0.0 or higher
- **PostgreSQL**: Version 14 or higher
- **Git**: Latest version
- **Docker** (Optional but recommended)

### Verification
```bash
node --version      # Should be v18+
npm --version       # Should be v9+
psql --version      # Should be 14+
git --version       # Latest
docker --version    # Latest (optional)
```

## 🚀 Installation Steps

### Step 1: Clone Repository
```bash
git clone https://github.com/vishwasmali4342/watar-tank.git
cd watar-tank
```

### Step 2: Environment Configuration

#### Create .env file
```bash
cp .env.example .env
```

#### Edit .env file with your credentials
```bash
# Use your preferred editor
nano .env
# or
code .env
# or
vim .env
```

**Required Credentials:**
- Firebase API Keys
- Google Maps API Key
- Razorpay Keys
- Database URL
- JWT Secret (min 32 characters)

### Step 3: Database Setup

#### Option A: Using Docker (Recommended)
```bash
# Start PostgreSQL, Redis, and pgAdmin
docker-compose up -d

# Verify containers are running
docker-compose ps
```

**Access pgAdmin:**
- URL: http://localhost:5050
- Email: admin@example.com
- Password: admin123

#### Option B: Manual PostgreSQL Setup
```bash
# Create database
psql -U postgres
CREATE DATABASE kcs_db;
CREATE USER kcsuser WITH PASSWORD 'kcspassword123';
GRANT ALL PRIVILEGES ON DATABASE kcs_db TO kcsuser;
\q
```

### Step 4: Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Create .env.local file
cp .env.local.example .env.local
# Edit with your credentials
nano .env.local

# Run development server
npm run dev

# Frontend available at: http://localhost:3000
```

### Step 5: Backend Setup

```bash
cd ../backend

# Install dependencies
npm install

# Run database migrations
npm run migrate

# Start development server
npm run start:dev

# Backend available at: http://localhost:3001
# API Docs: http://localhost:3001/api/docs
```

## ⚙️ Third-Party Service Configuration

### Firebase Setup
1. Go to [Firebase Console](https://console.firebase.google.com)
2. Create new project or use existing
3. Enable Authentication:
   - Email/Password
   - Google OAuth
   - Phone Authentication
4. Get credentials:
   - Project ID
   - API Key
   - Auth Domain
5. Download service account key (for backend)
6. Update .env files

### Google Maps API
1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Create new project
3. Enable APIs:
   - Maps JavaScript API
   - Directions API
   - Geocoding API
   - Distance Matrix API
4. Create API key
5. Restrict key to web applications
6. Update .env files

### Razorpay Setup
1. Create account at [Razorpay](https://razorpay.com)
2. Go to Dashboard → Settings → API Keys
3. Copy Key ID and Key Secret
4. Update .env file
5. Enable Test Mode for development

### Twilio Setup (SMS)
1. Create account at [Twilio](https://www.twilio.com)
2. Get Account SID and Auth Token
3. Get or create phone number
4. Update .env file

### SMTP Setup (Email)
```bash
# Using Gmail:
1. Enable 2-Factor Authentication
2. Create App Password
3. Update .env:
   SMTP_USER=your_email@gmail.com
   SMTP_PASS=your_app_password

# Or use any other SMTP provider
```

## 🧪 Verification

### Check Frontend
```bash
curl http://localhost:3000
# Should return HTML
```

### Check Backend
```bash
curl http://localhost:3001/api/health
# Should return: {"status":"OK","timestamp":"..."}
```

### Check Database
```bash
psql -U kcsuser -d kcs_db -c "SELECT version();"
```

### Check API Documentation
- Visit: http://localhost:3001/api/docs

## 📦 Building for Production

### Frontend Build
```bash
cd frontend
npm run build
npm start
```

### Backend Build
```bash
cd backend
npm run build
npm run start:prod
```

## 🐳 Docker Deployment

### Build Docker Images
```bash
# Frontend
docker build -f frontend/Dockerfile -t kcs-frontend .

# Backend
docker build -f backend/Dockerfile -t kcs-backend .
```

### Run with Docker Compose
```bash
docker-compose -f docker-compose.prod.yml up -d
```

## 🔧 Troubleshooting

### Port Already in Use
```bash
# Linux/Mac
lsof -i :3000
lsof -i :3001
lsof -i :5432

# Kill process
kill -9 <PID>

# Windows
netstat -ano | findstr :3000
taskkill /PID <PID> /F
```

### Database Connection Error
```bash
# Check PostgreSQL is running
sudo systemctl status postgresql

# Check credentials
psql -U kcsuser -d kcs_db

# Verify DATABASE_URL in .env
```

### Module Not Found
```bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install

# Clear Next.js cache
rm -rf .next
```

### Firebase Authentication Issues
```bash
# Verify credentials
firebase login
firebase projects:list

# Check .env file for correct values
# Ensure service account key is in backend directory
```

### CORS Issues
```bash
# Check FRONTEND_URL in backend .env
# Should match your frontend URL
# Default: http://localhost:3000
```

### Migration Fails
```bash
# Reset database (careful!)
npm run prisma:reset

# Or manually:
dropdb kcs_db
createdb kcs_db
npm run migrate
```

## 📚 Useful Commands

### Frontend
```bash
npm run dev          # Development
npm run build        # Production build
npm run lint         # Linting
npm run type-check   # TypeScript check
```

### Backend
```bash
npm run start:dev    # Development
npm run build        # Build
npm run test         # Tests
npm run migrate      # Database migration
npm run seed         # Seed database
```

### Database
```bash
npm run prisma:generate   # Generate Prisma client
npm run migrate          # Run migrations
npm run migrate:prod     # Production migration
```

## ✅ Final Checklist

- [ ] Node.js 18+ installed
- [ ] PostgreSQL running
- [ ] .env file configured with all credentials
- [ ] Firebase project created and configured
- [ ] Google Maps API key obtained
- [ ] Razorpay account set up
- [ ] Frontend dependencies installed
- [ ] Backend dependencies installed
- [ ] Database migrations run
- [ ] Frontend running on http://localhost:3000
- [ ] Backend running on http://localhost:3001
- [ ] API docs accessible
- [ ] Database connected and verified

## 🎉 Next Steps

1. Create test users (Customer, Technician, Admin)
2. Add test services (Water Tank, Solar Panel)
3. Test booking flow
4. Test payment integration
5. Test live tracking features
6. Review API documentation
7. Deploy to development/staging server

## 📞 Support

For issues:
1. Check [Troubleshooting](#-troubleshooting) section
2. Check logs: `docker-compose logs -f service_name`
3. Create GitHub issue with details
4. Contact development team

---

**Happy coding! 🚀**
