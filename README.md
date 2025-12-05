# Four Brothers Sports Center - E-Commerce Platform

A complete full-stack e-commerce platform for a Tanzanian sports shoe store, featuring customer and admin interfaces with **password-based authentication**, real-time order tracking, and comprehensive product management with **size-based inventory**.

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
- **🛒 Smart Shopping Cart** - Real-time quantity and size management
- **📏 Size Selection** - Choose from available sizes with stock tracking
- **💰 Cash on Delivery** - COD payment system optimized for Tanzania
- **📊 Order Tracking** - Real-time status updates (Imewekwa → Imepokelewa)
- **⭐ Product Ratings** - 5-star rating system with detailed feedback
- **🔄 Easy Returns** - 3-day return window with condition checks
- **📢 Live Announcements** - In-app notifications from admin
- **🌓 Dark/Light Mode** - Theme toggle for better UX
- **🔍 Product Search** - Instant search with filtering
- **🔐 Password Verification** - Required for order confirmation
- **🔄 Password Reset** - Secure password and mobile number recovery

### 👨‍💼 Admin Features
- **🔐 Secure Admin Login** - Multi-admin system with password authentication
- **📈 Analytics Dashboard** - Sales charts, revenue tracking, customer insights
- **📦 Product Management** - Full CRUD with Cloudinary image upload and size inventory
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
│     Browser     │────▶│  (Images)       │────▶│     (Email)     │
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
```

## 🗄️ Database Schema

### Core Tables Structure (Based on Actual Database Dump)

```sql
-- ==================== USERS (ADMINS) ====================
CREATE TABLE `users` (
  `id` int NOT NULL AUTO_INCREMENT,
  `first_name` varchar(50) NOT NULL,
  `last_name` varchar(50) NOT NULL,
  `mobile` varchar(20) NOT NULL,
  `password` varchar(255) NOT NULL,
  `is_admin` tinyint(1) DEFAULT '0',
  `can_manage_admins` tinyint(1) DEFAULT '0',
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `mobile` (`mobile`)
) ENGINE=MyISAM AUTO_INCREMENT=9 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== CUSTOMERS ====================
CREATE TABLE `customers` (
  `id` int unsigned NOT NULL AUTO_INCREMENT,
  `first_name` varchar(100) NOT NULL,
  `last_name` varchar(100) NOT NULL,
  `phone` varchar(20) NOT NULL,
  `password` varchar(255) NOT NULL,
  `reset_token` varchar(100) DEFAULT NULL,
  `reset_token_expires` datetime DEFAULT NULL,
  `email` varchar(150) DEFAULT NULL,
  `gender` enum('mwanaume','mwanamke','nyengine') NOT NULL,
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  `address` text,
  PRIMARY KEY (`id`),
  UNIQUE KEY `phone` (`phone`)
) ENGINE=InnoDB AUTO_INCREMENT=18 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== PRODUCTS ====================
CREATE TABLE `products` (
  `id` int NOT NULL AUTO_INCREMENT,
  `name` varchar(100) NOT NULL,
  `company` varchar(100) NOT NULL,
  `color` varchar(50) DEFAULT NULL,
  `discount_percent` int DEFAULT '0',
  `type` enum('Njumu','Trainer','Njumu na Trainer') NOT NULL,
  `price` decimal(10,2) NOT NULL,
  `description` text,
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=35 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== PRODUCT SIZES ====================
CREATE TABLE `product_sizes` (
  `id` int NOT NULL AUTO_INCREMENT,
  `product_id` int NOT NULL,
  `size_code` varchar(10) NOT NULL,
  `size_label` varchar(50) NOT NULL,
  `stock` int DEFAULT '0',
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `unique_product_size` (`product_id`,`size_code`),
  CONSTRAINT `product_sizes_ibfk_1` FOREIGN KEY (`product_id`) REFERENCES `products` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=41 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== PRODUCT IMAGES ====================
CREATE TABLE `product_images` (
  `id` int NOT NULL AUTO_INCREMENT,
  `product_id` int NOT NULL,
  `image_url` varchar(255) NOT NULL,
  PRIMARY KEY (`id`),
  KEY `product_id` (`product_id`)
) ENGINE=InnoDB AUTO_INCREMENT=92 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== ORDERS ====================
CREATE TABLE `orders` (
  `id` int NOT NULL AUTO_INCREMENT,
  `customer_id` int NOT NULL,
  `total_price` decimal(12,2) NOT NULL,
  `status` enum('Imewekwa','Inasafirishwa','Imepokelewa','Imepokelewa_PENDING','Ghairishwa','Kurudishwa') NOT NULL DEFAULT 'Imewekwa',
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `fk_orders_customer` (`customer_id`)
) ENGINE=InnoDB AUTO_INCREMENT=17 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== ORDER ITEMS (WITH SIZES) ====================
CREATE TABLE `order_items` (
  `id` int NOT NULL AUTO_INCREMENT,
  `order_id` int NOT NULL,
  `product_id` int NOT NULL,
  `size_id` int DEFAULT NULL,
  `quantity` int NOT NULL DEFAULT '1',
  `unit_price` decimal(12,2) NOT NULL,
  `line_total` decimal(12,2) NOT NULL,
  PRIMARY KEY (`id`),
  KEY `fk_order_items_order` (`order_id`),
  KEY `fk_order_items_product` (`product_id`),
  CONSTRAINT `fk_oi_order` FOREIGN KEY (`order_id`) REFERENCES `orders` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=17 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== ORDER RATINGS ====================
CREATE TABLE `order_ratings` (
  `id` int NOT NULL AUTO_INCREMENT,
  `order_id` int NOT NULL,
  `customer_id` int NOT NULL,
  `package_rating` tinyint NOT NULL,
  `delivery_rating` tinyint NOT NULL,
  `product_rating` tinyint NOT NULL,
  `overall_comment` text,
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `unique_order_customer` (`order_id`,`customer_id`),
  UNIQUE KEY `unique_order_rating` (`order_id`,`customer_id`),
  KEY `customer_id` (`customer_id`)
) ENGINE=InnoDB AUTO_INCREMENT=10 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== ADS ====================
CREATE TABLE `ads` (
  `id` int NOT NULL AUTO_INCREMENT,
  `image_url` varchar(255) NOT NULL,
  `link` varchar(255) DEFAULT NULL,
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=14 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== ADMIN NOTIFICATIONS ====================
CREATE TABLE `admin_notifications` (
  `id` int NOT NULL AUTO_INCREMENT,
  `content` text NOT NULL,
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  `type` enum('email','announcement') NOT NULL DEFAULT 'announcement',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=14 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== CUSTOMER NOTIFICATIONS ====================
CREATE TABLE `customer_notifications` (
  `id` int NOT NULL AUTO_INCREMENT,
  `customer_id` int NOT NULL,
  `message` text NOT NULL,
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `customer_id` (`customer_id`)
) ENGINE=InnoDB AUTO_INCREMENT=32 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== ORDER NOTIFICATIONS ====================
CREATE TABLE `order_notifications` (
  `id` int NOT NULL AUTO_INCREMENT,
  `order_id` int NOT NULL,
  `admin_viewed` tinyint(1) DEFAULT '0',
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `order_id` (`order_id`),
  CONSTRAINT `order_notifications_ibfk_1` FOREIGN KEY (`order_id`) REFERENCES `orders` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=14 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== MESSAGES ====================
CREATE TABLE `messages` (
  `id` int NOT NULL AUTO_INCREMENT,
  `content` text NOT NULL,
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ==================== CUSTOMER NOTIFICATION LOGS ====================
CREATE TABLE `customer_notification_logs` (
  `id` int NOT NULL AUTO_INCREMENT,
  `customer_notification_id` int NOT NULL,
  `admin_viewed` tinyint(1) DEFAULT '0',
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `customer_notification_id` (`customer_notification_id`),
  CONSTRAINT `customer_notification_logs_ibfk_1` FOREIGN KEY (`customer_notification_id`) REFERENCES `customer_notifications` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
```

## 🔄 Relationships Diagram

```
users (admins)
    ↓
    | (no direct foreign key to customers/orders)
    |
customers
    ↓ (1:m)
orders
    ↓ (1:m)
order_items
    ├───→ products
    └───→ product_sizes (via size_id)
            ↑
            | (belongs to)
        product_sizes
            ↑ (1:m)
        products
            ↓ (1:m)
        product_images
            └───→ product_sizes
```

## 📊 Sample Data Structure

### Products with Sizes (Example from Database)
```sql
-- Product: Nike 2 (ID: 32)
INSERT INTO products (name, company, color, type, price) 
VALUES ('Nike 2', 'Nike', 'Nyeupe', 'Trainer', 65000.00);

-- Product Sizes for Nike 2
INSERT INTO product_sizes (product_id, size_code, size_label, stock) VALUES
(32, '40', 'EU 40', 5),
(32, '42', 'EU 42', 3);

-- Product Images for Nike 2
INSERT INTO product_images (product_id, image_url) VALUES
(32, 'https://res.cloudinary.com/dmluieytq/image/upload/v1764871340/products/ubmlamsiwfhfjghkdfyf.jpg');
```

### Orders with Size Selection (Example)
```sql
-- Order with multiple items and sizes
INSERT INTO orders (customer_id, total_price, status) 
VALUES (17, 553500.00, 'Imepokelewa');

-- Order Items with specific sizes
INSERT INTO order_items (order_id, product_id, size_id, quantity, unit_price, line_total) VALUES
(16, 32, 21, 7, 60000.00, 420000.00),  -- size_id 21 = EU 40
(16, 33, 25, 3, 65000.00, 195000.00);  -- size_id 25 = EU 40 (from product 33)
```

## 🚀 Quick Start

### For Customers
1. Visit **https://fourbrothers.online**
2. Register with your phone number and password
3. Login with phone and password
4. Browse products, select sizes, add to cart
5. Checkout and track orders

### For Admins
1. Visit **https://fourbrothers.online/admin.html**
2. Login with phone number and password
3. Access dashboard, manage products, track orders

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
# Import the schema using the provided SQL dump
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

# Admin Default Credentials
DEFAULT_ADMIN_MOBILE=+255777730606
DEFAULT_ADMIN_PASSWORD=admin123
```

### Step 5: Initialize Admin User
After setting up the database, create the initial admin user:

```sql
-- Insert initial admin (ID: 1 with can_manage_admins=1)
INSERT INTO users (first_name, last_name, mobile, password, is_admin, can_manage_admins) 
VALUES ('Mohammed', 'Shehe', '+255777730606', '$2b$10$jJTrGY8T0gXwUTq4oQasCuBNz4eZb4Fl.PXO819ssh0RjgGZ/Ha8S', 1, 1);
```

**Note:** The password hash shown is for `admin123`. You can generate your own using bcrypt.

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

## 📚 API Documentation

### Base URL: `https://api.fourbrothers.online/api`

### Customer Endpoints (`/customers`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/register` | Register new customer with password | No |
| POST | `/login` | Login with phone and password | No |
| POST | `/refresh-token` | Refresh access token with refresh token | No |
| GET | `/products` | Get all products with sizes and images | No |
| GET | `/products/:id` | Get specific product with sizes and images | No |
| POST | `/orders` | Place new order (with size selection) | Yes |
| GET | `/orders` | Get customer's orders with items and sizes | Yes |
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
| GET | `/dashboard/stats` | Dashboard statistics | Yes |
| GET | `/products` | Get all products | Yes |
| POST | `/products` | Add new product with images and sizes | Yes |
| PUT | `/products/:id` | Update product | Yes |
| DELETE | `/products/:id` | Delete product | Yes |
| POST | `/products/:id/sizes` | Add/update product sizes | Yes |
| GET | `/customers` | Get all customers | Yes |
| GET | `/orders` | Get all orders | Yes |
| PUT | `/orders/:order_id/status` | Update order status | Yes |
| GET | `/ads` | Get all ads | Yes |
| POST | `/ads` | Upload ad banner | Yes |
| DELETE | `/ads/:id` | Delete ad | Yes |
| GET | `/admins` | Get all admins (main admin only) | Yes |
| POST | `/admins` | Add new admin (main admin only) | Yes |
| PUT | `/admins/:id` | Update admin (main admin only) | Yes |
| DELETE | `/admins/:id` | Delete admin (main admin only) | Yes |

## 🔍 Key Features Explained

### Size-Based Inventory System
- Each product can have multiple sizes (EU 40, EU 42, etc.)
- Each size has its own stock count
- When customers order, they select specific sizes
- Stock is decremented per size when orders are placed
- Admin can manage stock per size for each product

### Order Status Flow with Password Verification
```
Imewekwa (Order Placed) 
    ↓
Inasafirishwa (Shipping in Progress) 
    ↓
Imepokelewa_PENDING (Delivered, awaiting customer confirmation)
    ↓ (Customer enters password)
Imepokelewa (Order Received & Confirmed) 
    ↓
Ghairishwa (Cancelled) / Kurudishwa (Returned)
```

**Important:** Customers confirm order receipt by entering their password, providing an extra security layer.

### Rating System
Customers can rate three aspects after receiving their order:
1. **Package Rating** - Quality of packaging
2. **Delivery Rating** - Delivery experience
3. **Product Rating** - Product quality
4. **Overall Comment** - General feedback

### Product Types
- **Njumu** - Formal/dress shoes
- **Trainer** - Sports/sneakers
- **Njumu na Trainer** - Both types available

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
5. **Initialize database** using the provided SQL dump
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

### 4. Custom Domain Setup (Optional)

1. **Purchase domain** from registrar
2. **Configure DNS:**
   - Add CNAME record for `www` pointing to `[username].github.io`
   - Add A records for root domain pointing to GitHub IPs
3. **Configure GitHub Pages:**
   - Add custom domain in repository settings
   - Enable HTTPS enforcement
4. **Update backend CORS** to allow custom domain

## 🔐 Security Features

### Password Security
- **Bcrypt hashing** for all passwords
- **Password verification** for order confirmation
- **Password reset tokens** with expiration (1 hour)
- **Current password required** for sensitive changes

### Authentication
- **JWT tokens** with 7-day expiration
- **Refresh tokens** for extended sessions
- **Role-based access control** for admins
- **Main admin protection** (ID: 1 cannot be deleted)

### Data Protection
- **Environment variables** for sensitive data
- **Input validation** on all endpoints
- **SQL injection prevention** via parameterized queries
- **File upload restrictions** (size: 5MB, types: jpg, png, jpeg)

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

## 📞 Support

For technical support or questions about the platform:

1. **GitHub Issues:** Open an issue in the relevant repository
   - Frontend issues: [FourBrothersSportsCenter Issues](https://github.com/MohammedShehe/FourBrothersSportsCenter/issues)
   - Backend issues: [FourBrothersSportsCenter-Backend Issues](https://github.com/MohammedShehe/FourBrothersSportsCenter-Backend/issues)

   **All rights reserved © 2025 Four Brothers Sports Center**

---

## 🤝 Contributing
While this is primarily a commercial project, bug reports and suggestions are welcome through GitHub Issues.

**Made with ❤️ in Tanzania 🇹🇿**  
*Empowering local businesses through technology*  
*Bridging the digital divide in retail commerce*  
*Supporting Tanzanian entrepreneurship and innovation*

---

## 🔄 Version History

### Version 1.0.0 (December 2025) - **PRODUCTION RELEASE**
**Complete E-commerce Platform with Password-Based Authentication & Size Inventory**

#### ✅ Key Features
- **🔐 Password-Based Authentication System**
- **📏 Size-Based Inventory Management**
- **🛒 Complete Shopping Experience with Size Selection**
- **📊 Comprehensive Admin Dashboard**
- **🔧 Full Technical Implementation with PostgreSQL**

#### 🚀 Deployment Status
- **Frontend:** ✅ Deployed to GitHub Pages (https://fourbrothers.online)
- **Backend:** ✅ Deployed to Render (https://api.fourbrothers.online)
- **Database:** ✅ PostgreSQL on Railway
- **Authentication:** ✅ Password-based system

**Last Updated:** December 5, 2025  
**Version:** 1.0.0  
**Status:** Production Ready  

---

*This platform represents a significant step forward in digitizing retail commerce in Tanzania, providing local businesses with tools previously available only to large corporations. By making e-commerce accessible and affordable, we're helping Tanzanian entrepreneurs compete in the digital economy.*