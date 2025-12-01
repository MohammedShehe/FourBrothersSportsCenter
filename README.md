# Four Brothers Sports Center - E-Commerce Platform

A complete full-stack e-commerce platform for a Tanzanian sports shoe store, featuring customer and admin interfaces with SMS OTP authentication, real-time order tracking, and comprehensive product management.

## 🚀 Live Applications
Platform	URL

Customer Portal	https://fourbrothers.online

Admin Panel	https://fourbrothers.online/admin.html

Backend API	https://api.fourbrothers.online

Frontend Repository	https://github.com/MohammedShehe/FourBrothersSportsCenter

Backend Repository	https://github.com/MohammedShehe/FourBrothersSportsCenter-Backend


## ✨ Features

### 🛍️ Customer Features
- **📱 Phone Authentication** - OTP verification via Twilio SMS
- **🛒 Smart Shopping Cart** - Real-time quantity management
- **💰 Cash on Delivery** - COD payment system optimized for Tanzania
- **📊 Order Tracking** - Real-time status updates (Imewekwa → Imepokelewa)
- **⭐ Product Ratings** - 5-star rating system with detailed feedback
- **🔄 Easy Returns** - 3-day return window with condition checks
- **📢 Live Announcements** - In-app notifications from admin
- **🌓 Dark/Light Mode** - Theme toggle for better UX
- **🔍 Product Search** - Instant search with filtering

### 👨‍💼 Admin Features
- **🔐 Secure Admin Login** - Multi-admin system with OTP verification
- **📈 Analytics Dashboard** - Sales charts, revenue tracking, customer insights
- **📦 Product Management** - Full CRUD with Cloudinary image upload
- **👥 Customer Management** - View, add, and manage customers
- **📊 Order Management** - Update statuses, generate OTPs for delivery
- **📢 Ad Management** - Upload promotional banners with clickable links
- **📱 Bulk Messaging** - Send announcements to all/specific customers
- **⚙️ Status Control** - Manage order lifecycle with visual indicators

## 🛠️ Tech Stack

### Frontend (GitHub Pages)
- **HTML5, CSS3, JavaScript (ES6+)**
- **Bootstrap 5** - Responsive design framework
- **Chart.js** - Dashboard visualizations
- **Font Awesome 6** - Icon library
- **Local Storage** - Client-side persistence

### Backend (Render)
- **Node.js** - Runtime environment
- **Express.js** - REST API framework
- **JWT** - Secure authentication
- **Multer** - File upload middleware
- **Twilio API** - SMS OTP delivery
- **Nodemailer** - Email notifications

### Database (Railway)
- **PostgreSQL** - Production database
- **MySQL** - Local development option

### Cloud Services
- **Cloudinary** - Image storage and CDN
- **GitHub Pages** - Frontend hosting
- **Render** - Backend API hosting
- **Railway** - Database hosting

## 📊 Architecture Diagram

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│                 │     │                 │     │                 │
│   GitHub Pages  │────▶│   Render API    │────▶│   Railway DB    │
│  (Frontend)     │     │  (Backend)      │     │  (PostgreSQL)   │
│                 │     │                 │     │                 │
└─────────────────┘     └─────────────────┘     └─────────────────┘
         │                        │                        │
         │                        │                        │
         ▼                        ▼                        ▼
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│                 │     │                 │     │                 │
│    Customer     │     │  Cloudinary     │     │    Twilio       │
│     Browser     │────▶│  (Images)       │     │    (SMS)        │
│                 │     │                 │     │                 │
└─────────────────┘     └─────────────────┘     └─────────────────┘
```

## 📁 Project Structure

### Frontend Repository (`FourBrothersSportsCenter`)
```
FourBrothersSportsCenter/
├── index.html                     # Main customer interface
├── admin.html                     # Admin panel interface
├── regulations.html               # Terms & conditions
├── images/                        # Static assets
│   └── FBSC.png                   # Logo
└── (Pure HTML/CSS/JS - no build step)
```

### Backend Repository (`FourBrothersSportsCenter-Backend`)
```
FourBrothersSportsCenter-Backend/
├── config/
│   ├── database.js               # Database connection
│   ├── multer.js                 # File upload config
│   └── cloudinary.js             # Cloudinary setup
├── controllers/
│   ├── adminController.js        # Admin logic
│   ├── customerController.js     # Customer logic
│   ├── dashboardController.js    # Dashboard stats
│   ├── productController.js      # Product CRUD
│   └── notificationController.js # Ads & notifications
├── middlewares/
│   ├── adminAuth.js              # Admin JWT auth
│   └── customerAuth.js           # Customer JWT auth
├── routes/
│   ├── adminRoutes.js            # Admin API endpoints
│   └── customerRoutes.js         # Customer API endpoints
├── utils/
│   ├── helpers.js                # OTP, SMS, Email helpers
│   ├── otp.js                    # OTP generation logic
│   └── otpCleaner.js            # Cron job for cleanup
├── .env                          # Environment variables
├── package.json                  # Dependencies
├── server.js                     # Express server
└── four_brothers.sql             # MySQL schema (for reference)
```

## 🚀 Quick Start

### For Customers
1. Visit **https://fourbrothers.online**
2. Register with your phone number
3. Verify OTP sent via SMS
4. Start shopping!

### For Admins
1. Visit **https://fourbrothers.online/admin.html**
**
2. Login with First Name + Last Name
3. Check SMS for OTP verification
4. Access dashboard

## 💻 Local Development Setup

### Prerequisites
- Node.js (v16 or higher)
- Git
- MySQL or PostgreSQL (for local development)
- Twilio Account (for SMS functionality)
- Cloudinary Account (for image storage)

### Step 1: Clone Repositories
```bash
# Clone frontend repository
git clone https://github.com/MohammedShehe/FourBrothersSportsCenter.git
cd FourBrothersSportsCenter

# Clone backend repository (in separate terminal or directory)
git clone https://github.com/MohammedShehe/FourBrothersSportsCenter-Backend.git
cd FourBrothersSportsCenter-Backend
```

### Step 2: Backend Setup
```bash
# Install backend dependencies
cd FourBrothersSportsCenter-Backend
npm install
```

### Step 3: Database Setup
**Option A: Local MySQL (Development)**
```bash
# Import the schema
mysql -u root -p < four_brothers.sql
```

**Option B: Railway PostgreSQL (Production Parity)**
1. Create account at [railway.app](https://railway.app)
2. Create new PostgreSQL project
3. Get connection string from Railway dashboard

### Step 4: Environment Configuration
Create a `.env` file in the backend directory with the following variables:

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database Configuration
DATABASE_URL=your_database_connection_string

# JWT Configuration
JWT_SECRET=your_jwt_secret
JWT_REFRESH_SECRET=your_refresh_secret
JWT_EXPIRES_IN=1h

# OTP Configuration
OTP_LENGTH=6
OTP_EXPIRES_MINUTES=5

# Service Credentials (obtain from respective providers)
TWILIO_ACCOUNT_SID=your_twilio_sid
TWILIO_AUTH_TOKEN=your_twilio_token
TWILIO_PHONE_NUMBER=your_twilio_number

CLOUDINARY_CLOUD_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_key
CLOUDINARY_API_SECRET=your_cloudinary_secret

# Email Configuration (Optional)
EMAIL_USER=your_email
EMAIL_PASS=your_email_password
```

### Step 5: Frontend Configuration
Update the API URL in the frontend files to point to your local backend:

In both `index.html` and `admin.html`, find and update:
```javascript
const API_BASE_URL = 'http://localhost:5000/api';
```

### Step 6: Run Development Servers
```bash
# Start backend server
cd FourBrothersSportsCenter-Backend
npm run dev

# Frontend - serve using any static server
# Option 1: Python simple server
cd FourBrothersSportsCenter
python -m http.server 8000

# Option 2: Node http-server
npm install -g http-server
http-server -p 8000
```

Now access:
- **Customer Portal:** http://localhost:8000
- **Admin Panel:** http://localhost:8000/admin.html
- **Backend API:** http://localhost:5000/api

## 🗄️ Database Schema

### Core Tables Structure
```sql
-- Customers table
CREATE TABLE customers (
    id SERIAL PRIMARY KEY,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    phone VARCHAR(20) UNIQUE NOT NULL,
    email VARCHAR(150),
    gender VARCHAR(20),
    address TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Products table
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    company VARCHAR(100) NOT NULL,
    color VARCHAR(50),
    discount_percent INTEGER DEFAULT 0,
    type VARCHAR(50),
    size_us VARCHAR(10),
    stock INTEGER DEFAULT 0,
    price DECIMAL(10,2) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Orders table
CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    customer_id INTEGER REFERENCES customers(id),
    total_price DECIMAL(12,2) NOT NULL,
    status VARCHAR(50) DEFAULT 'Imewekwa',
    otp VARCHAR(6),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Additional tables: product_images, order_items, order_ratings, ads, notifications
```

### Order Status Flow
```
Imewekwa (Order Placed) 
    ↓
Inasafirishwa (Shipping in Progress) 
    ↓
Imepokelewa_PENDING (Awaiting Customer Confirmation) 
    ↓
Imepokelewa (Order Received & Confirmed) 
    ↓
Ghairishwa (Cancelled) / Kurudishwa (Returned)
```

## 📚 API Documentation

### Base URL: `https://fourbrotherssportscenter-backend.onrender.com/api`

### Customer Endpoints (`/customers`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/register` | Register new customer | No |
| POST | `/send-otp` | Send login OTP to phone | No |
| POST | `/verify-otp` | Verify OTP & get access tokens | No |
| POST | `/refresh-token` | Refresh access token | Yes |
| GET | `/me` | Get customer profile | Yes |
| PUT | `/me/update` | Update customer profile | Yes |
| GET | `/products` | Get all products | No |
| GET | `/products/:id` | Get specific product | No |
| POST | `/orders` | Place new order | Yes |
| GET | `/orders` | Get customer's orders | Yes |
| POST | `/orders/:id/cancel` | Cancel order | Yes |
| POST | `/orders/:id/return` | Request return | Yes |
| POST | `/orders/:id/rate` | Rate completed order | Yes |
| GET | `/ratings` | Get product ratings | Yes |
| GET | `/ads` | Get active ads | No |
| GET | `/announcements` | Get announcements | Yes |
| POST | `/send-message` | Send message to admin | Yes |

### Admin Endpoints (`/admin`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/login` | Request admin OTP | No |
| POST | `/verify-otp` | Verify admin OTP | No |
| GET | `/dashboard/stats` | Dashboard statistics | Yes |
| GET | `/products` | Get all products | Yes |
| POST | `/products` | Add new product | Yes |
| PUT | `/products/:id` | Update product | Yes |
| DELETE | `/products/:id` | Delete product | Yes |
| GET | `/customers` | Get all customers | Yes |
| POST | `/customers` | Add customer | Yes |
| PUT | `/customers/:id` | Update customer | Yes |
| DELETE | `/customers/:id` | Delete customer | Yes |
| GET | `/ads` | Get all ads | Yes |
| POST | `/ads` | Upload ad banner | Yes |
| DELETE | `/ads/:id` | Delete ad | Yes |
| GET | `/orders` | Get all orders | Yes |
| PUT | `/orders/:order_id/status` | Update order status | Yes |
| POST | `/orders/:order_id/generate-otp` | Generate delivery OTP | Yes |
| POST | `/orders/:order_id/confirm` | Confirm order reception | Yes |
| GET | `/notifications/customer` | View customer messages | Yes |
| POST | `/notifications/send` | Send announcements | Yes |
| POST | `/messages` | Post in-app announcements | Yes |

## 🚀 Deployment Guide

### 1. Backend Deployment (Render)

1. **Push backend code to GitHub**
2. **Go to [render.com](https://render.com)**
3. **Create new Web Service**
4. **Connect your backend GitHub repository**
5. **Configure service settings:**
   - **Name:** `four-brothers-backend` (or your preferred name)
   - **Environment:** `Node`
   - **Build Command:** `npm install`
   - **Start Command:** `node server.js`
   - **Plan:** Free
6. **Add Environment Variables** in Render dashboard (copy from your `.env` file)
7. **Deploy** and note the generated URL

### 2. Database Deployment (Railway)

1. **Create account at [railway.app](https://railway.app)**
2. **Create new project**
3. **Add PostgreSQL database**
4. **Get connection string** from Overview tab
5. **Update backend** `DATABASE_URL` environment variable with Railway connection string
6. **Initialize database** by running the SQL schema

### 3. Frontend Deployment (GitHub Pages)

1. **Ensure frontend files** are in the root of `FourBrothersSportsCenter` repository
2. **Go to repository Settings → Pages**
3. **Configure GitHub Pages:**
   - **Source:** `Deploy from a branch`
   - **Branch:** `main` (or your default branch)
   - **Folder:** `/` (root directory)
4. **Save** - Your site will be available at `https://[username].github.io/FourBrothersSportsCenter/`
5. **Update API URL** in frontend files to point to your Render backend

### 4. Service Configuration

#### Cloudinary Setup
1. **Create account at [cloudinary.com](https://cloudinary.com)**
2. **Get credentials** from Dashboard
3. **Add to backend environment variables:**
   - `CLOUDINARY_CLOUD_NAME`
   - `CLOUDINARY_API_KEY`
   - `CLOUDINARY_API_SECRET`

#### Twilio Setup
1. **Create account at [twilio.com](https://twilio.com)**
2. **Purchase Tanzanian phone number**
3. **Get credentials:**
   - `TWILIO_ACCOUNT_SID`
   - `TWILIO_AUTH_TOKEN`
   - `TWILIO_PHONE_NUMBER`

### 5. Final Configuration

1. **Update frontend API URL** in both `index.html` and `admin.html`:
```javascript
const API_BASE_URL = 'https://[your-render-backend].onrender.com/api';
```

2. **Configure CORS** in backend to allow your GitHub Pages domain:
```javascript
app.use(cors({
  origin: ['https://mohammedshehe.github.io'],
  credentials: true
}));
```

3. **Test all connections:**
   - Test customer registration (SMS OTP)
   - Test admin login (SMS OTP)
   - Test image upload (Cloudinary)
   - Test order placement (Database)

## 📱 Usage Guide

### For Store Owners (Admin)

1. **Access Admin Panel**
   - Visit: `https://fourbrothers.online/admin.html`
   - Login with First Name + Last Name of registered admin

2. **Manage Products**
   - Add new sports shoes with images
   - Set prices, sizes, and stock levels
   - Apply discounts and categorize products

3. **Track Orders**
   - View all customer orders
   - Update order status as they progress
   - Generate OTPs for delivery confirmation

4. **Customer Management**
   - View registered customers
   - Add new customers manually
   - Send announcements to specific customers

5. **Analytics & Dashboard**
   - Monitor sales revenue
   - Track product performance
   - View customer growth

### For Customers

1. **Browse Products**
   - Visit: `https://fourbrothers.online`
   - Filter by size, brand, or type
   - View product details and images

2. **Account Creation**
   - Register with phone number
   - Verify OTP sent via SMS
   - Complete profile with address

3. **Shopping Experience**
   - Add products to cart
   - Select sizes and quantities
   - Apply cart discounts (10% for 3+ items)

4. **Checkout Process**
   - Provide delivery address
   - Confirm order details
   - Choose Cash on Delivery

5. **Order Tracking**
   - View order history in account
   - Track current order status
   - Rate products after delivery

6. **Returns & Support**
   - Request returns within 3 days
   - Contact support via in-app messaging
   - View announcements from store

### Order Status Meanings

| Status | Meaning | Customer Action Required |
|--------|---------|--------------------------|
| **Imewekwa** | Order placed | None - waiting for processing |
| **Inasafirishwa** | Order shipped | Prepare for delivery |
| **Imepokelewa_PENDING** | Delivery pending | Enter OTP to confirm receipt |
| **Imepokelewa** | Order received | Rate products (optional) |
| **Ghairishwa** | Order cancelled | None |
| **Kurudishwa** | Product returned | None |

## 🔍 Troubleshooting

### Common Issues & Solutions

#### 1. SMS OTP Not Sending
**Symptoms:** Customer doesn't receive OTP for registration/login
**Solutions:**
- Verify Twilio credentials are correct in environment variables
- Ensure phone number is in correct format: `+255XXXXXXXXX`
- Check Twilio account balance and phone number capability
- Test with Tanzanian phone numbers (some carriers may have delays)

#### 2. Database Connection Issues
**Symptoms:** "Cannot connect to database" errors
**Solutions:**
- Verify `DATABASE_URL` is correct in environment variables
- Check if Railway PostgreSQL instance is running
- Ensure database tables are initialized with SQL schema
- Test connection locally before deploying

#### 3. Image Upload Failing
**Symptoms:** Product images not uploading or displaying
**Solutions:**
- Verify Cloudinary credentials are correct
- Check file size (max 5MB per image)
- Ensure correct image formats (jpg, png, jpeg)
- Test Cloudinary upload in development first

#### 4. CORS Errors in Browser Console
**Symptoms:** Frontend cannot connect to backend API
**Solutions:**
- Ensure CORS is configured in backend to allow GitHub Pages domain
- Update `API_BASE_URL` in frontend to correct backend URL
- Check if backend is running and accessible
- Verify no typos in API endpoint URLs

#### 5. GitHub Pages Showing 404
**Symptoms:** Customer portal not loading
**Solutions:**
- Ensure `index.html` is in root of repository
- Check GitHub Pages configuration in repository settings
- Wait 1-2 minutes after changes for GitHub Pages to update
- Clear browser cache and try again

#### 6. Admin Login Issues
**Symptoms:** Admin cannot login or OTP not received
**Solutions:**
- Verify admin account exists in `users` table with `is_admin=1`
- Check Twilio phone number can send to admin's number
- Ensure admin's mobile number in database matches login attempt
- Try resending OTP after 2 minutes

### Development Debugging Tips

1. **Check Server Logs:**
```bash
# For Render backend
# View logs in Render dashboard

# For local development
cd FourBrothersSportsCenter-Backend
npm run dev
# Check console output for errors
```

2. **Test API Endpoints:**
```bash
# Using curl to test endpoints
curl -X GET https://your-backend.onrender.com/api/customers/products
curl -X POST https://your-backend.onrender.com/api/customers/send-otp \
  -H "Content-Type: application/json" \
  -d '{"phone": "+255777730606"}'
```

3. **Database Inspection:**
```sql
-- Connect to Railway PostgreSQL
psql $DATABASE_URL

-- Check tables
\dt

-- Sample queries
SELECT * FROM customers LIMIT 5;
SELECT * FROM products WHERE stock > 0;
SELECT status, COUNT(*) FROM orders GROUP BY status;
```

## 🤝 Contributing

We welcome contributions to improve the Four Brothers Sports Center platform!

### How to Contribute

1. **Fork the repositories:**
   - Frontend: [FourBrothersSportsCenter](https://github.com/MohammedShehe/FourBrothersSportsCenter)
   - Backend: [FourBrothersSportsCenter-Backend](https://github.com/MohammedShehe/FourBrothersSportsCenter-Backend)

2. **Create a feature branch:**
```bash
git checkout -b feature/amazing-feature
```

3. **Make your changes** following the existing code style

4. **Test thoroughly:**
   - Test frontend changes in multiple browsers
   - Test backend endpoints with Postman or curl
   - Ensure database migrations (if any) work correctly

5. **Commit with descriptive message:**
```bash
git commit -m "Add: Feature description"
```

6. **Push to your fork:**
```bash
git push origin feature/amazing-feature
```

7. **Open a Pull Request** with clear description of changes

### Development Guidelines

- **Code Style:** Follow existing patterns and indentation
- **Comments:** Add comments for complex logic or business rules
- **Documentation:** Update relevant documentation with changes
- **Testing:** Test features thoroughly before submitting
- **Security:** Never commit credentials or sensitive data
- **Performance:** Consider efficiency for Tanzanian network conditions

### Areas for Contribution

1. **Frontend Improvements:**
   - Better mobile responsiveness
   - Additional filtering options
   - Enhanced product search
   - Improved user onboarding

2. **Backend Features:**
   - Additional analytics endpoints
   - Bulk operations for admin
   - Enhanced error handling
   - Performance optimizations

3. **Documentation:**
   - API documentation improvements
   - Deployment guides for other regions
   - Translation to other languages

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

**MIT License Summary:**
- ✅ Commercial use allowed
- ✅ Modification allowed
- ✅ Distribution allowed
- ✅ Private use allowed
- ❌ No liability
- ❌ No warranty

## 👥 Team & Contact

- **Store:** Four Brothers Sports Center
- **Location:** Tanzania
- **Industry:** Sports Footwear Retail
- **Focus:** Quality sports shoes at affordable prices

### Contact Information
For business inquiries or technical support:
- **Email:** Available upon request
- **Phone:** Available upon request
- **Location:** Tanzania

### Development Team
This platform was developed to support local Tanzanian businesses in establishing their online presence and reaching more customers through digital channels.

## 🙏 Acknowledgments

We gratefully acknowledge the services and communities that made this project possible:

- **Render** for providing reliable backend hosting
- **Railway** for excellent PostgreSQL database service
- **GitHub** for free static site hosting via GitHub Pages
- **Cloudinary** for robust image storage and CDN
- **Twilio** for reliable SMS delivery services
- **Bootstrap** for responsive design framework
- **Chart.js** for data visualization components
- **Font Awesome** for comprehensive icon library

Special thanks to the open-source community for the countless tools and libraries that power modern web development.

## 📞 Support

For technical support or questions about the platform:

1. **GitHub Issues:** Open an issue in the relevant repository
   - Frontend issues: [FourBrothersSportsCenter Issues](https://github.com/MohammedShehe/FourBrothersSportsCenter/issues)
   - Backend issues: [FourBrothersSportsCenter-Backend Issues](https://github.com/MohammedShehe/FourBrothersSportsCenter-Backend/issues)

2. **Documentation:** Refer to this README and code comments

3. **Community:** Share experiences and solutions with other users

### Support Guidelines
- **Bug Reports:** Include steps to reproduce, expected vs actual behavior
- **Feature Requests:** Describe the need and potential implementation
- **Questions:** Check documentation first, then ask specific questions
- **Response Time:** Allow 2-3 business days for responses

---

**Made with ❤️ in Tanzania 🇹🇿**  
*Empowering local businesses through technology*  
*Bridging the digital divide in retail commerce*  
*Supporting Tanzanian entrepreneurship and innovation*

---

## 🔄 Update Log

### Version 1.0.0 (Current - November 2025)
**Initial Release - Production Ready**

#### ✅ Completed Features
- **Core E-commerce Platform**
  - Complete customer portal with product browsing
  - Full admin panel with dashboard
  - Multi-admin system with OTP authentication

- **Customer Features**
  - Phone-based registration with SMS OTP
  - Shopping cart with quantity management
  - Order tracking with real-time status
  - Product ratings and reviews system
  - 3-day return policy implementation

- **Admin Features**
  - Product management with image upload
  - Customer management system
  - Order management with status control
  - Ad and announcement system
  - Sales analytics dashboard

- **Technical Implementation**
  - Full-stack architecture (Frontend + Backend + Database)
  - Cloud deployment (GitHub Pages + Render + Railway)
  - Image storage (Cloudinary)
  - SMS integration (Twilio)
  - Responsive design for all devices

#### 🚀 Deployment Status
- **Frontend:** ✅ Deployed to GitHub Pages
- **Backend:** ✅ Deployed to Render
- **Database:** ✅ Configured with Railway PostgreSQL
- **Services:** ✅ Integrated with Cloudinary and Twilio

### Planned Features (Future Releases)

#### Version 1.1.0 (Q1 2026)
- [ ] Mobile application (React Native/Flutter)
- [ ] Push notifications for order updates
- [ ] Advanced product filtering and sorting
- [ ] Wishlist functionality

#### Version 1.2.0 (Q2 2026)
- [ ] Payment gateway integration (M-Pesa, Airtel Money)
- [ ] Inventory management with alerts
- [ ] Sales analytics with advanced reports
- [ ] Customer loyalty program

#### Version 1.3.0 (Q3 2026)
- [ ] Multi-vendor support
- [ ] Advanced search with AI recommendations
- [ ] Multi-language support (Swahili, English)
- [ ] Social media integration

#### Version 2.0.0 (Q4 2026)
- [ ] Progressive Web App (PWA) features
- [ ] Offline functionality
- [ ] Advanced shipping and logistics integration
- [ ] API documentation portal

### Version History

| Version | Date | Key Changes | Status |
|---------|------|-------------|--------|
| 1.0.0 | Nov 2025 | Initial production release | ✅ Current |
| 0.9.0 | Oct 2025 | Beta testing and bug fixes | ✅ Completed |
| 0.8.0 | Sep 2025 | Admin panel development | ✅ Completed |
| 0.7.0 | Aug 2025 | Customer portal development | ✅ Completed |
| 0.6.0 | Jul 2025 | Backend API development | ✅ Completed |
| 0.5.0 | Jun 2025 | Database design and setup | ✅ Completed |
| 0.1.0 | May 2025 | Project initialization and planning | ✅ Completed |

---

**Last Updated:** November 30, 2025  
**Version:** 1.0.0  
**Status:** Production Ready  
**Next Release:** Version 1.1.0 (Q1 2026)

---

*This platform represents a significant step forward in digitizing retail commerce in Tanzania, providing local businesses with tools previously available only to large corporations. By making e-commerce accessible and affordable, we're helping Tanzanian entrepreneurs compete in the digital economy.*