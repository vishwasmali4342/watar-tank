# KCS Water Tank & Solar Panel Cleaning - Service Marketplace Platform

🚀 **Premium Urban Company-style Service Marketplace** for Water Tank & Solar Panel Cleaning with scalable architecture.

## 📋 Features Overview

### 🎯 Customer Features
- ✅ OTP & Google Login
- ✅ Service Selection & Booking
- ✅ Google Maps Address Selection
- ✅ Date-Time Scheduling
- ✅ Live GPS Tracking
- ✅ Real-time ETA Updates
- ✅ In-App Live Chat
- ✅ Push Notifications
- ✅ Online Payments (Razorpay)
- ✅ Booking History & Re-booking
- ✅ Digital Invoices & Receipts
- ✅ Before/After Photos
- ✅ Ratings & Reviews
- ✅ Referral Program
- ✅ Multi-language (English, Hindi, Marathi)

### 👨‍🔧 Technician Features
- ✅ Secure Login with OTP
- ✅ Today's Jobs Dashboard
- ✅ Job Accept/Reject
- ✅ Google Maps Navigation
- ✅ Live Location Sharing
- ✅ Before/After Photo Upload
- ✅ Customer Signature Capture
- ✅ Earnings Dashboard
- ✅ Attendance & Leave Management
- ✅ Push Notifications

### 👨‍💼 Super Admin Dashboard
- ✅ Real-time Analytics Dashboard
- ✅ Customer Management
- ✅ Technician Management & Verification
- ✅ Order Management
- ✅ Live Technician Tracking
- ✅ Pricing Control with Manual Override
- ✅ Coupons & Offers Management
- ✅ Payment & Payout Management
- ✅ Reports & Analytics
- ✅ Role-Based Access Control

## 🛠 Technology Stack

| Component | Technology |
|-----------|------------|
| **Frontend** | Next.js 14, React 18, TypeScript, Tailwind CSS |
| **Backend** | NestJS, Express.js, TypeScript |
| **Database** | PostgreSQL 15, Prisma ORM |
| **Real-time** | Socket.IO for live tracking & chat |
| **Authentication** | Firebase OTP, Google OAuth, JWT |
| **Payments** | Razorpay Integration |
| **Maps** | Google Maps API with Live GPS |
| **Notifications** | Firebase Cloud Messaging, SMTP, Twilio SMS |
| **Deployment** | Docker, CI/CD Ready, Cloud-Ready |

## 📁 Project Structure

```
watar-tank/
├── frontend/                    # Next.js Customer & Admin Web App
│   ├── src/
│   │   ├── pages/              # Page routes
│   │   ├── components/         # Reusable components
│   │   ├── stores/             # Zustand state management
│   │   ├── types/              # TypeScript types
│   │   └── utils/              # Helper functions
│   ├── public/                 # Static assets
│   └── package.json
│
├── backend/                     # NestJS Backend API
│   ├── src/
│   │   ├── auth/               # Authentication module
│   │   ├── users/              # User management
│   │   ├── services/           # Service module
│   │   ├── bookings/           # Booking management
│   │   ├── payments/           # Payment processing
│   │   └── main.ts             # Entry point
│   └── package.json
│
├── database/                    # Database configuration
│   ├── schema.prisma           # Prisma schema
│   └── migrations/             # DB migrations
│
├── docker-compose.yml          # Docker setup
├── .env.example                # Environment template
└── README.md
```

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- PostgreSQL 15+
- Docker & Docker Compose (optional)
- Git

### Installation

```bash
# 1. Clone repository
git clone https://github.com/vishwasmali4342/watar-tank.git
cd watar-tank

# 2. Copy environment file
cp .env.example .env

# 3. Start database with Docker
docker-compose up -d

# 4. Install & run frontend
cd frontend
npm install
npm run dev
# Frontend: http://localhost:3000

# 5. Install & run backend (new terminal)
cd backend
npm install
npm run migrate      # Run database migrations
npm run start:dev
# Backend: http://localhost:3001
# API Docs: http://localhost:3001/api/docs
```

## 📚 Documentation

- [Setup Guide](./docs/SETUP_GUIDE.md) - Detailed installation & configuration
- [API Documentation](./docs/API_DOCUMENTATION.md) - All API endpoints
- [Database Schema](./database/schema.prisma) - Database structure
- [Deployment Guide](./docs/DEPLOYMENT.md) - Production deployment

## 🔐 Environment Variables

Create `.env` file:

```env
# Frontend
NEXT_PUBLIC_API_URL=http://localhost:3001
NEXT_PUBLIC_FIREBASE_API_KEY=your_key
NEXT_PUBLIC_GOOGLE_MAPS_API_KEY=your_key
NEXT_PUBLIC_RAZORPAY_KEY_ID=your_key

# Backend
DATABASE_URL=postgresql://user:password@localhost:5432/kcs_db
JWT_SECRET=your_secret_min_32_chars
FIREBASE_PROJECT_ID=your_project
RAZORPAY_KEY_ID=your_key
RAZORPAY_KEY_SECRET=your_secret
```

## 🚢 Deployment

### Docker Deployment
```bash
docker-compose -f docker-compose.yml up -d
```

### AWS/Google Cloud/Azure
See [DEPLOYMENT.md](./docs/DEPLOYMENT.md) for detailed instructions

## 🧪 Testing

```bash
# Run all tests
npm run test

# Test coverage
npm run test:cov

# E2E tests
npm run test:e2e
```

## 📊 API Endpoints

### Authentication
- `POST /api/auth/register/customer` - Register customer
- `POST /api/auth/login` - Login
- `POST /api/auth/verify-otp` - OTP verification

### Services
- `GET /api/services` - Get all services
- `GET /api/services/:id` - Get service details

### Bookings
- `POST /api/bookings` - Create booking
- `GET /api/bookings` - Get customer bookings
- `PUT /api/bookings/:id/cancel` - Cancel booking

### Payments
- `POST /api/payments/create-order` - Create Razorpay order
- `POST /api/payments/verify` - Verify payment

### More endpoints in [API_DOCUMENTATION.md](./docs/API_DOCUMENTATION.md)

## 🎯 Roadmap

- ✅ Phase 1: Water Tank & Solar Panel Cleaning
- 🔄 Phase 2: Car Wash, Sofa Cleaning, Pest Control
- 🔄 Phase 3: AC Service, Plumbing, Electrical
- 🔄 Phase 4: Advanced Analytics & AI Features
- 🔄 Phase 5: Mobile App (React Native)

## 🤝 Contributing

1. Fork repository
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open Pull Request

## 📝 License

MIT License - feel free to use this project

## 💬 Support

For questions or issues:
- Create GitHub Issue
- Check [Troubleshooting Guide](./docs/SETUP_GUIDE.md#troubleshooting)
- Contact: support@kcsservices.com

## 👥 Team

Built with ❤️ by KCS Development Team

---

**Made with ❤️ for Urban Cleaners**
