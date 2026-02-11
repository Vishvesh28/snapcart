# 🛒 SnapCart

A modern, full-stack grocery delivery platform built with Next.js 16, featuring real-time order tracking, geolocation-based delivery assignment, and integrated payment processing.

![Next.js](https://img.shields.io/badge/Next.js-16.0-black?style=flat-square&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue?style=flat-square&logo=typescript)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-green?style=flat-square&logo=mongodb)
![Stripe](https://img.shields.io/badge/Stripe-Payments-purple?style=flat-square&logo=stripe)

## ✨ Features

### 🎯 Multi-Role System
- **Users**: Browse groceries, add to cart, place orders, track deliveries in real-time
- **Delivery Personnel**: Receive assignments, navigate to delivery locations, manage deliveries
- **Admins**: Manage inventory, assign deliveries, monitor platform analytics

### 🚀 Core Capabilities
- **Real-time Tracking**: Live delivery tracking with Socket.io integration
- **Geolocation Services**: Location-based delivery assignment using Leaflet maps
- **Smart Search**: Search groceries by name or category
- **Payment Integration**: Stripe payment gateway with webhook support
- **Authentication**: Secure auth with NextAuth.js (Google OAuth + credentials)
- **OTP Verification**: Delivery confirmation via OTP system
- **Live Chat**: Real-time messaging between users and delivery personnel
- **Responsive Design**: Mobile-first design with Tailwind CSS

### 📦 Product Categories
- Fruits & Vegetables
- Dairy & Eggs
- Rice, Atta & Grains
- Snacks & Biscuits
- Spices & Masalas
- Beverages & Drinks
- Personal Care
- Household Essentials
- Instant & Packaged Food
- Baby & Pet Care

## 🛠️ Tech Stack

### Frontend
- **Framework**: Next.js 16 (App Router)
- **Language**: TypeScript
- **Styling**: Tailwind CSS 4
- **UI Components**: Lucide React icons
- **Animations**: Motion (Framer Motion)
- **State Management**: Redux Toolkit
- **Maps**: Leaflet + React Leaflet
- **Charts**: Recharts

### Backend
- **Runtime**: Node.js
- **Database**: MongoDB (Mongoose ODM)
- **Authentication**: NextAuth.js v5
- **Payment**: Stripe
- **Real-time**: Socket.io Client
- **Image Upload**: Cloudinary
- **Email**: Nodemailer

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- **Node.js** (v18 or higher)
- **npm** or **yarn** or **pnpm**
- **MongoDB Atlas** account (or local MongoDB)
- **Stripe** account
- **Cloudinary** account
- **Google OAuth** credentials

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone <repository-url>
cd 1.snapcart
```

### 2. Install Dependencies
```bash
npm install
# or
yarn install
# or
pnpm install
```

### 3. Environment Setup

Create a `.env.local` file in the root directory with the following variables:

```env
# Database
MONGODB_URL="your_mongodb_connection_string"

# Authentication
AUTH_SECRET="your_auth_secret_key"
GOOGLE_CLIENT_ID="your_google_client_id"
GOOGLE_CLIENT_SECRET="your_google_client_secret"

# Cloudinary (Image Upload)
CLOUDINARY_CLOUD_NAME="your_cloudinary_cloud_name"
CLOUDINARY_API_KEY="your_cloudinary_api_key"
CLOUDINARY_API_SECRET="your_cloudinary_api_secret"

# Stripe (Payments)
STRIPE_SECRET_KEY="your_stripe_secret_key"
STRIPE_WEBHOOK_SECRET="your_stripe_webhook_secret"

# Application
NEXT_BASE_URL="http://localhost:3000"

# Socket.io Server
NEXT_PUBLIC_SOCKET_SERVER="http://localhost:4000"

# Gemini API (Optional - for AI features)
GEMINI_API_KEY="your_gemini_api_key"

# Email (Nodemailer)
EMAIL="your_email@gmail.com"
PASS="your_app_password"
```

### 4. Run the Development Server

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser to see the application.

### 5. Setup Socket.io Server (Required for Real-time Features)

The application requires a separate Socket.io server running on port 4000 for real-time features like live tracking and chat. Make sure to set up and run the Socket.io server before using real-time features.

## 📁 Project Structure

```
1.snapcart/
├── src/
│   ├── app/                    # Next.js App Router
│   │   ├── api/               # API routes
│   │   ├── admin/             # Admin dashboard
│   │   ├── user/              # User pages
│   │   ├── login/             # Login page
│   │   └── register/          # Registration page
│   ├── components/            # React components
│   │   ├── AdminDashboard.tsx
│   │   ├── UserDashboard.tsx
│   │   ├── DeliveryBoy.tsx
│   │   ├── Nav.tsx
│   │   └── ...
│   ├── models/                # Mongoose models
│   │   ├── user.model.ts
│   │   ├── grocery.model.ts
│   │   ├── order.model.ts
│   │   └── deliveryAssignment.model.ts
│   ├── lib/                   # Utility functions
│   ├── redux/                 # Redux store & slices
│   ├── hooks/                 # Custom React hooks
│   └── auth.ts               # NextAuth configuration
├── public/                    # Static assets
├── .env.local                # Environment variables
└── package.json              # Dependencies
```

## 🔑 Key Features Explained

### Authentication Flow
1. Users can sign up with email/password or Google OAuth
2. After registration, users complete their profile (mobile number, role selection)
3. Role-based access control restricts features based on user type

### Order Flow
1. **User**: Browse groceries → Add to cart → Checkout with address
2. **Payment**: Choose COD or online payment (Stripe)
3. **Admin**: View pending orders → Assign to nearby delivery personnel
4. **Delivery**: Accept assignment → Navigate to location → Deliver with OTP
5. **Completion**: User verifies delivery with OTP → Order marked as delivered

### Geolocation Features
- Users' locations are tracked for delivery assignment
- Delivery personnel can see live navigation to delivery addresses
- Admin can assign orders to the nearest available delivery person
- 2D sphere indexing on MongoDB for efficient geospatial queries

## 🔧 Available Scripts

```bash
# Development
npm run dev          # Start development server

# Production
npm run build        # Build for production
npm run start        # Start production server

# Code Quality
npm run lint         # Run ESLint
```

## 🌐 API Routes

### User Routes
- `POST /api/auth/signup` - User registration
- `POST /api/auth/login` - User login
- `GET /api/user/orders` - Get user orders
- `POST /api/user/checkout` - Create new order

### Admin Routes
- `GET /api/admin/orders` - Get all orders
- `POST /api/admin/assign-delivery` - Assign delivery
- `GET /api/admin/analytics` - Platform analytics

### Stripe Webhooks
- `POST /api/user/stripe/webhook` - Handle Stripe payment events

## 🎨 UI Components

The application features a modern, responsive design with:
- **Dark/Light mode** support
- **Animated transitions** using Motion
- **Interactive maps** with Leaflet
- **Real-time updates** via Socket.io
- **Mobile-responsive** navigation and layouts

## 🔐 Security Features

- Password hashing with bcryptjs
- JWT-based authentication
- CSRF protection with NextAuth
- Stripe webhook signature verification
- Environment variable protection
- Role-based access control

## 📊 Database Schema

### User Model
- Name, email, password (hashed)
- Mobile number, role (user/deliveryBoy/admin)
- Geolocation (2dsphere indexed)
- Socket ID for real-time features

### Grocery Model
- Name, category, price, unit
- Image URL (Cloudinary)
- Timestamps

### Order Model
- User reference
- Items array (grocery details + quantity)
- Payment method (COD/online)
- Delivery address with coordinates
- Status (pending/out of delivery/delivered)
- Delivery OTP verification

## 🚢 Deployment

### Vercel (Recommended)
1. Push your code to GitHub
2. Import project in Vercel
3. Add environment variables
4. Deploy

### Manual Deployment
```bash
npm run build
npm run start
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request





