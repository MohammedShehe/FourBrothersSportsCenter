# Four Brothers Sports Center - E-Commerce Platform

A complete full-stack e-commerce platform for a Tanzanian sports shoe store, featuring customer and admin interfaces with **password-based authentication**, real-time order tracking, and comprehensive product management.

## 🚀 Live Applications

| Platform | URL |
|----------|-----|
| **Customer Portal** | [https://fourbrothers.online](https://fourbrothers.online) |
| **Admin Panel** | [https://fourbrothers.online/admin.html](https://fourbrothers.online/admin.html) |
| **Backend API** | [https://api.fourbrothers.online](https://api.fourbrothers.online) |
| **Frontend Repository** | [https://github.com/MohammedShehe/FourBrothersSportsCenter](https://github.com/MohammedShehe/FourBrothersSportsCenter) |
| **Backend Repository** | [https://github.com/MohammedShehe/FourBrothersSportsCenter-Backend](https://github.com/MohammedShehe/FourBrothersSportsCenter-Backend) |

## ✨ Features

### 🛍️ Customer Features
- **🔐 Password Authentication** - Secure registration and login with password verification
- **🛒 Smart Shopping Cart** - Real-time quantity management with 10% discount for 3+ items
- **💰 Cash on Delivery** - COD payment system optimized for Tanzania
- **📊 Order Tracking** - Real-time status updates (Imewekwa → Imepokelewa)
- **⭐ Product Ratings** - 5-star rating system with detailed feedback
- **🔄 Easy Returns** - 3-day return window with condition checks
- **📢 Live Announcements** - In-app notifications from admin
- **🌓 Dark/Light Mode** - Theme toggle for better UX
- **🔍 Product Search** - Instant search with filtering
- **🔐 Password Verification** - Required for first order confirmation
- **🔄 Password Reset** - Secure password and mobile number recovery

### 👨‍💼 Admin Features
- **🔐 Secure Admin Login** - Multi-admin system with password authentication
- **📈 Analytics Dashboard** - Sales charts, revenue tracking, customer insights
- **📦 Product Management** - Full CRUD with Cloudinary image upload
- **👥 Customer Management** - View, add, and manage customers
- **📊 Order Management** - Update statuses, track shipments
- **📢 Ad Management** - Upload promotional banners with clickable links
- **📱 Bulk Messaging** - Send announcements to all/specific customers
- **👑 Admin Management** - Add/edit/delete admins (main admin only)
- **📧 Email Notifications** - Send bulk emails to customers
- **💬 Customer Support** - View and respond to customer messages

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
- **JWT** - Secure authentication with refresh tokens
- **Multer** - File upload middleware
- **Bcrypt** - Password hashing and verification
- **Nodemailer** - Email notifications
- **MySQL/PostgreSQL** - Database support

### Database (Railway)
- **PostgreSQL** - Production database (Railway)
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
│    Customer     │     │  Cloudinary     │     │     Nodemailer  │
│     Browser     │────▶│  (Images)       │     │     (Email)     │
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
│   ├── customerFunctionalities.js # Customer logic
│   ├── dashboardController.js    # Dashboard stats
│   ├── productController.js      # Product CRUD
│   └── notificationController.js # Ads & notifications
├── middlewares/
│   ├── adminAuth.js              # Admin JWT auth
│   └── customerAuth.js           # Customer JWT auth (access + refresh tokens)
├── routes/
│   ├── adminRoutes.js            # Admin API endpoints
│   └── customerRoutes.js         # Customer API endpoints
├── utils/
│   └── helpers.js                # Email, phone normalization helpers
├── .env                          # Environment variables
├── package.json                  # Dependencies
├── server.js                     # Express server
├── four_brothers.sql             # MySQL schema (for reference)
└── railway_schema.sql           # PostgreSQL schema for production
```

## 🚀 Quick Start

### For Customers
1. Visit **https://fourbrothers.online**
2. Register with your phone number and password
3. Login with phone and password
4. Start shopping!

### For Admins
1. Visit **https://fourbrothers.online/admin.html**
2. Login with phone number and password
3. Access dashboard

## 💻 Local Development Setup

### Prerequisites
- Node.js (v16 or higher)
- Git
- MySQL or PostgreSQL (for local development)
- Cloudinary Account (for image storage)
- Gmail account (for email notifications - optional)

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

# Database Configuration (Railway PostgreSQL example)
DB_HOST=containers-us-west-XXX.railway.app
DB_USER=postgres
DB_PASSWORD=your_password
DB_NAME=railway
DB_PORT=XXXXX

# JWT Configuration
JWT_SECRET=your_jwt_secret_key_here
JWT_EXPIRES_IN=7d
JWT_REFRESH_SECRET=your_refresh_secret_key_here

# Cloudinary Configuration
CLOUDINARY_CLOUD_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

# Email Configuration (Optional - for admin announcements)
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_app_specific_password

# Admin Default Credentials (first admin)
DEFAULT_ADMIN_MOBILE=+255777730606
DEFAULT_ADMIN_PASSWORD=admin123
```

### Step 5: Initialize Admin User
After setting up the database, create the initial admin user:

```bash
# The first admin (ID: 1) will be created with can_manage_admins=1
# You can also insert manually using SQL:
INSERT INTO users (first_name, last_name, mobile, password, is_admin, can_manage_admins) 
VALUES ('Mohammed', 'Shehe', '+255777730606', '$2b$10$YourHashedPassword', 1, 1);
```

### Step 6: Frontend Configuration
Update the API URL in the frontend files to point to your local backend:

In both `index.html` and `admin.html`, find and update:
```javascript
const API_BASE_URL = 'http://localhost:5000/api';
```

### Step 7: Run Development Servers
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
-- Customers table (with password authentication)
CREATE TABLE customers (
    id SERIAL PRIMARY KEY,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    phone VARCHAR(20) UNIQUE NOT NULL,
    email VARCHAR(150),
    gender VARCHAR(20),
    address TEXT,
    password VARCHAR(255) NOT NULL,
    reset_token VARCHAR(100),
    reset_token_expires TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Users table (for admins)
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    mobile VARCHAR(20) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    is_admin BOOLEAN DEFAULT FALSE,
    can_manage_admins BOOLEAN DEFAULT FALSE,
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

-- Orders table (NO OTP column - using password verification)
CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    customer_id INTEGER REFERENCES customers(id),
    total_price DECIMAL(12,2) NOT NULL,
    status VARCHAR(50) DEFAULT 'Imewekwa',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Additional tables:
-- product_images, order_items, order_ratings, ads, admin_notifications, customer_notifications
```

### Order Status Flow
```
Imewekwa (Order Placed) 
    ↓
Inasafirishwa (Shipping in Progress) 
    ↓
Imepokelewa (Order Received & Confirmed via Password) 
    ↓
Ghairishwa (Cancelled) / Kurudishwa (Returned)
```

**Important Change:** The `Imepokelewa_PENDING` status has been removed. Customers now verify order receipt by entering their password instead of an OTP.

## 📚 API Documentation

### Base URL: `https://api.fourbrothers.online/api`

### Customer Endpoints (`/customers`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/register` | Register new customer with password | No |
| POST | `/login` | Login with phone and password | No |
| POST | `/refresh-token` | Refresh access token with refresh token | No |
| POST | `/forgot-password` | Request password reset via name verification | No |
| POST | `/reset-password` | Reset password with reset token | No |
| POST | `/change-mobile` | Change phone number via name verification | No |
| GET | `/me` | Get customer profile | Yes |
| PUT | `/me/update` | Update customer profile | Yes |
| POST | `/me/change-email` | Change email (requires current password) | Yes |
| POST | `/me/change-phone` | Change phone (requires current password) | Yes |
| POST | `/me/change-password` | Change password (requires current password) | Yes |
| GET | `/products` | Get all products | No |
| GET | `/products/:id` | Get specific product | No |
| POST | `/orders` | Place new order | Yes |
| GET | `/orders` | Get customer's orders | Yes |
| POST | `/orders/:id/cancel` | Cancel order with reason | Yes |
| POST | `/orders/:id/return` | Request return (within 3 days) | Yes |
| POST | `/orders/:id/rate` | Rate completed order | Yes |
| GET | `/ratings` | Get product ratings | Yes |
| GET | `/ads` | Get active ads | No |
| GET | `/announcements` | Get announcements | Yes |
| POST | `/send-message` | Send message to admin | Yes |
| POST | `/verify-password` | Verify password for order confirmation | Yes |
| POST | `/orders/:id/confirm` | Confirm order reception with password | Yes |

### Admin Endpoints (`/admin`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/login` | Admin login with phone and password | No |
| POST | `/forgot-password` | Request admin password reset | No |
| POST | `/reset-password` | Reset admin password | No |
| POST | `/change-mobile` | Change admin phone number | No |
| GET | `/dashboard/stats` | Dashboard statistics | Yes |
| GET | `/products` | Get all products | Yes |
| POST | `/products` | Add new product with images | Yes |
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
| GET | `/notifications/customer` | View customer messages | Yes |
| POST | `/notifications/send` | Send announcements via email | Yes |
| POST | `/messages` | Post in-app announcements | Yes |
| GET | `/admins` | Get all admins (main admin only) | Yes |
| POST | `/admins` | Add new admin (main admin only) | Yes |
| PUT | `/admins/:id` | Update admin (main admin only) | Yes |
| DELETE | `/admins/:id` | Delete admin (main admin only) | Yes |

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
7. **Deploy** and note the generated URL (e.g., `https://four-brothers-backend.onrender.com`)

### 2. Database Deployment (Railway)

1. **Create account at [railway.app](https://railway.app)**
2. **Create new project**
3. **Add PostgreSQL database**
4. **Get connection string** from Overview tab
5. **Initialize database** using the provided SQL schema
6. **Update backend** environment variables with Railway connection details

### 3. Frontend Deployment (GitHub Pages)

1. **Update API URLs** in frontend files:
   - In `index.html` and `admin.html`, change:
   ```javascript
   const API_BASE_URL = 'https://your-render-backend.onrender.com/api';
   ```
2. **Commit and push** changes to GitHub
3. **Go to repository Settings → Pages**
4. **Configure GitHub Pages:**
   - **Source:** `Deploy from a branch`
   - **Branch:** `main` (or your default branch)
   - **Folder:** `/` (root directory)
5. **Save** - Your site will be available at `https://[username].github.io/FourBrothersSportsCenter/`

### 4. Service Configuration

#### Cloudinary Setup
1. **Create account at [cloudinary.com](https://cloudinary.com)**
2. **Get credentials** from Dashboard
3. **Add to backend environment variables:**
   - `CLOUDINARY_CLOUD_NAME`
   - `CLOUDINARY_API_KEY`
   - `CLOUDINARY_API_SECRET`

#### Gmail Setup (for email notifications)
1. **Use Gmail account**
2. **Enable 2-factor authentication**
3. **Generate app-specific password**
4. **Add to backend environment variables:**
   - `EMAIL_USER` (your Gmail address)
   - `EMAIL_PASS` (app-specific password)

### 5. Final Configuration

1. **Configure CORS** in backend to allow your frontend domain:
```javascript
// In server.js
app.use(cors({
  origin: [
    'https://your-username.github.io',
    'https://fourbrothers.online' // Your custom domain if applicable
  ],
  credentials: true
}));
```

2. **Custom Domain (Optional):**
   - Purchase domain from registrar (e.g., Namecheap, GoDaddy)
   - Add CNAME record pointing to `your-username.github.io`
   - Configure in GitHub Pages settings

3. **Test all connections:**
   - Test customer registration and login
   - Test admin login
   - Test image upload
   - Test order placement

## 📱 Usage Guide

### For Store Owners (Admin)

1. **Access Admin Panel**
   - Visit: `https://fourbrothers.online/admin.html`
   - Login with registered admin phone and password

2. **Main Admin vs Regular Admin**
   - **Main Admin (ID: 1):** Can manage other admins (add/edit/delete)
   - **Regular Admin:** Can manage products, customers, orders, but not other admins

3. **Password Recovery Options**
   - Forgot password: Enter first and last name → Get reset options
   - Reset password or change phone number

4. **Manage Products**
   - Add new sports shoes with up to 5 images
   - Set prices, sizes, stock levels
   - Apply discounts
   - Categorize by type (Njumu, Trainer, Njumu na Trainer)

5. **Track Orders**
   - View all customer orders
   - Update order status (except "Imepokelewa" which requires customer password)
   - Monitor order progress

6. **Customer Management**
   - View registered customers
   - Add new customers manually
   - Send announcements via email or in-app messages

7. **Analytics & Dashboard**
   - Monitor sales revenue (current year)
   - Track total customers and products
   - View monthly income charts

### For Customers

1. **Account Creation**
   - Register with phone number and password
   - Provide name, address, gender
   - Email optional

2. **Password Security Features**
   - First order requires password verification for security
   - Can change password, email, or phone (requires current password)
   - Password reset via name verification

3. **Shopping Experience**
   - Browse products with images
   - Filter by type, brand, color
   - View stock availability
   - See product ratings

4. **Order Process**
   - Add to cart, select quantity and size
   - 10% discount automatically applied for 3+ items
   - Checkout with delivery address
   - First order: Password verification required
   - COD payment upon delivery

5. **Order Management**
   - View order history
   - Cancel orders (status: "Imewekwa" only)
   - Return orders within 3 days of receipt
   - Rate products after receiving

6. **Communication**
   - View announcements from store
   - Send messages to admin via app
   - Receive order updates

### Order Status Meanings

| Status | Meaning | Customer Action Required |
|--------|---------|--------------------------|
| **Imewekwa** | Order placed | None - waiting for processing |
| **Inasafirishwa** | Order shipped | Prepare for delivery |
| **Imepokelewa** | Order received | Enter password to confirm receipt |
| **Ghairishwa** | Order cancelled | None |
| **Kurudishwa** | Product returned | None |

**Important:** Customers confirm order receipt by entering their password, not an OTP.

## 🔍 Troubleshooting

### Common Issues & Solutions

#### 1. Login Issues
**Symptoms:** Cannot login with correct credentials
**Solutions:**
- Verify password is correct
- Check if account exists (customer or admin)
- Try password reset if forgotten
- Clear browser cache and cookies

#### 2. Database Connection Issues
**Symptoms:** "Cannot connect to database" errors
**Solutions:**
- Verify database credentials in `.env`
- Check if Railway PostgreSQL instance is running
- Ensure database tables are initialized
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
- Ensure CORS is configured in backend to allow frontend domain
- Update `API_BASE_URL` in frontend to correct backend URL
- Check if backend is running and accessible
- Verify no typos in API endpoint URLs

#### 5. Email Not Sending
**Symptoms:** Admin announcements not reaching customers
**Solutions:**
- Verify Gmail credentials are correct
- Ensure 2FA is enabled and app-specific password is used
- Check if customer has email address in their profile
- Test email functionality in development first

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
curl -X POST https://your-backend.onrender.com/api/customers/login \
  -H "Content-Type: application/json" \
  -d '{"phone": "+255777730606", "password": "test123"}'
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

## 🔐 Security Features

### Password Security
- **Bcrypt hashing** for all passwords
- **Password verification** for first order confirmation
- **Password reset tokens** with expiration
- **Current password required** for sensitive changes

### Authentication
- **JWT tokens** for API authentication
- **Refresh tokens** for extended sessions
- **Admin role-based access control**
- **Main admin protection** (ID: 1 cannot be deleted)

### Data Protection
- **Environment variables** for sensitive data
- **Input validation** on all endpoints
- **SQL injection prevention** via parameterized queries
- **File upload restrictions** (size, type)




## 👥 Team & Contact

- **Store:** Four Brothers Sports Center
- **Location:** Zanzibar, Tanzania
- **Industry:** Sports Footwear Retail
- **Focus:** Quality sports shoes at affordable prices

### Development Team
This platform was developed to support local Tanzanian businesses in establishing their online presence and reaching more customers through digital channels.

## 🙏 Acknowledgments

We gratefully acknowledge the services and communities that made this project possible:

- **Render** for providing reliable backend hosting
- **Railway** for excellent PostgreSQL database service
- **GitHub** for free static site hosting via GitHub Pages
- **Cloudinary** for robust image storage and CDN
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

### Version 2.0.0 (December 2025) - **PASSWORD-BASED AUTHENTICATION UPDATE**
**Major Security Update - Replaced OTP with Password System**

#### ✅ Major Changes from Version 1.0.0
- **🔐 Authentication Overhaul**
  - **REMOVED:** Twilio SMS OTP system completely
  - **ADDED:** Password-based registration and login for customers
  - **ADDED:** Password-based admin authentication
  - **ADDED:** Password verification for first order security
  - **ADDED:** Secure password reset via name verification

- **🔄 Token System Enhancement**
  - **ADDED:** JWT refresh token system for customers
  - **IMPROVED:** Token expiration and renewal process
  - **ENHANCED:** Security middleware for both customer and admin routes

- **👑 Admin Management System**
  - **ADDED:** Multi-admin support with role hierarchy
  - **ADDED:** Main admin (can_manage_admins=1) with full privileges
  - **ADDED:** Regular admin with limited privileges
  - **ADDED:** Admin management interface (add/edit/delete)

- **📱 Customer Experience Improvements**
  - **ADDED:** Profile management with password-protected changes
  - **ADDED:** Change email/phone with current password verification
  - **ADDED:** Password strength indicator during registration
  - **IMPROVED:** Password reset flow with name verification

- **📧 Enhanced Communication**
  - **ADDED:** Bulk email announcements from admin panel
  - **ADDED:** In-app messaging system
  - **ADDED:** Customer-to-admin message support
  - **IMPROVED:** Announcement display system

- **💾 Database Schema Updates**
  - **REMOVED:** OTP-related columns from orders table
  - **ADDED:** Password columns to customers and users tables
  - **ADDED:** Reset token system for password recovery
  - **ADDED:** Admin management columns in users table

#### 🚀 Deployment Status
- **Frontend:** ✅ Updated with new authentication flows
- **Backend:** ✅ Completely rewritten authentication system
- **Database:** ✅ Schema updated for password system
- **Services:** ✅ Removed Twilio dependency, added email support

### Version 1.0.0 (November 2025) - Initial Release
- Complete e-commerce platform with OTP authentication
- Admin panel with dashboard
- Product management system
- Order tracking with OTP delivery confirmation

### Planned Features (Future Releases)

#### Version 2.1.0 (Q1 2026)
- [ ] Mobile application (React Native/Flutter)
- [ ] Push notifications for order updates
- [ ] Advanced product filtering and sorting
- [ ] Wishlist functionality
- [ ] Customer loyalty program

#### Version 2.2.0 (Q2 2026)
- [ ] Payment gateway integration (M-Pesa, Airtel Money)
- [ ] Inventory management with alerts
- [ ] Sales analytics with advanced reports
- [ ] Multi-language support (Swahili, English)

#### Version 2.3.0 (Q3 2026)
- [ ] Multi-vendor support
- [ ] Advanced search with AI recommendations
- [ ] Social media integration
- [ ] Customer referral program

#### Version 3.0.0 (Q4 2026)
- [ ] Progressive Web App (PWA) features
- [ ] Offline functionality
- [ ] Advanced shipping and logistics integration
- [ ] API documentation portal

### Version History

| Version | Date | Key Changes | Status |
|---------|------|-------------|--------|
| 2.0.0 | Dec 2025 | Password-based authentication | ✅ Current |
| 1.0.0 | Nov 2025 | Initial production release with OTP | ✅ Completed |
| 0.9.0 | Oct 2025 | Beta testing and bug fixes | ✅ Completed |
| 0.8.0 | Sep 2025 | Admin panel development | ✅ Completed |
| 0.7.0 | Aug 2025 | Customer portal development | ✅ Completed |
| 0.6.0 | Jul 2025 | Backend API development | ✅ Completed |
| 0.5.0 | Jun 2025 | Database design and setup | ✅ Completed |
| 0.1.0 | May 2025 | Project initialization and planning | ✅ Completed |

---

**Last Updated:** December 3, 2025  
**Version:** 2.0.0  
**Status:** Production Ready  
**Next Release:** Version 2.1.0 (Q1 2026)

---

*This platform represents a significant step forward in digitizing retail commerce in Tanzania, providing local businesses with tools previously available only to large corporations. By making e-commerce accessible and affordable, we're helping Tanzanian entrepreneurs compete in the digital economy.*

**Key Security Note:** Version 2.0.0 replaces the SMS OTP system with a more secure and reliable password-based authentication system, reducing operational costs while improving user experience and security.