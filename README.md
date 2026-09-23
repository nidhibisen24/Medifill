# 🏥 MediFill – Online Healthcare & Medicine Platform

MediFill is a Django-based healthcare platform that brings medicine shopping, doctor discovery, appointment booking, shop-owner management, cart management, orders, shipping, and customer feedback together in one web application.

The platform allows customers to browse medicines, search for doctors, book appointments, manage their shopping cart, place orders, manage shipping information, and submit feedback.

---

## ✨ Features

### 👤 User Authentication
- Custom email-based user authentication
- User signup and login
- Logout functionality
- User profile management
- Password management
- Django Admin authentication

### 💊 Medicine & Product Management
- Medicine/product catalog
- Product categories
- Product variants
- Product detail pages
- Product search
- Product price and stock information
- Shop-owner product insertion

### 🛒 Shopping Cart
- Add products to cart
- Remove products from cart
- Cart item management
- Automatic cart total calculation
- Product variant support

### 👨‍⚕️ Doctor Module
- Doctor registration
- Doctor profiles
- Doctor search
- Doctor information
- Appointment booking

### 🏪 Shop Owner Module
- Shop-owner registration
- Shop-owner profiles
- Product insertion
- Product management

### 📦 Order & Shipping
- Order management
- Order item management
- Order amount tracking
- Order status tracking
- Payment status tracking
- Shipping address management

### 💳 Payment
- Payment page
- Unpaid cart detection
- Cart total calculation
- Payment status tracking

> **Note:** The current implementation prepares the payment flow but does not include a complete third-party payment gateway integration.

### ⭐ Customer Feedback
- Customer feedback submission
- Feedback management through Django Admin

### ⚙️ Admin Panel
- User management
- Product management
- Doctor management
- Order management
- Feedback management
- Shop management

---

## 🛠️ Technology Stack

| Technology | Purpose |
|------------|---------|
| Python | Backend programming |
| Django 4.2 | Web framework |
| HTML5 | Frontend structure |
| CSS3 | Styling |
| Django Templates | Frontend rendering |
| SQLite | Development database |
| Pillow | Image processing |
| Django Authentication | User authentication |
| Git & GitHub | Version control |

---

## 🏗️ Project Structure

```text
MediFill/
│
├── MediFill/
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── Home/
│   └── Authentication, users, profiles & homepage
│
├── Product/
│   └── Products, categories & variants
│
├── Cart/
│   └── Cart & cart items
│
├── Order/
│   └── Orders & order items
│
├── Payment/
│   └── Payment page & cart total
│
├── Doctor/
│   └── Doctors & appointments
│
├── Shop/
│   └── Shop-owner registration & products
│
├── Shipping/
│   └── Shipping addresses
│
├── Contact/
│   └── Customer feedback
│
├── templates/
│   └── Shared HTML templates
│
├── static/
│   └── CSS & image assets
│
├── manage.py
├── .gitignore
└── README.md
🔄 Application Flow
Customer Flow
User
  │
  ▼
Signup / Login
  │
  ▼
Browse Medicines
  │
  ▼
Search / Product Details
  │
  ▼
Add to Cart
  │
  ▼
Shopping Cart
  │
  ▼
Payment Page
  │
  ▼
Order
  │
  ▼
Shipping Address
  │
  ▼
Order Tracking
Doctor Flow
User
  │
  ▼
Search Doctors
  │
  ▼
Doctor Profile
  │
  ▼
Book Appointment
Shop Owner Flow
Shop Owner
  │
  ▼
Register Shop
  │
  ▼
Shop Owner Profile
  │
  ▼
Add Products
  │
  ▼
Manage Products
🗃️ Data Model

The major relationships between the application entities are:

CustomUser
├── Doctor
├── ShopOwner
├── Carts
└── Appointment

Product_Category
└── Product
    └── Product_Variant

Carts
└── CartItems
    ├── Product
    └── Product_Variant

Orders
├── OrderItems
└── Shipping_addresses
Important Models
Model	Purpose
Home.CustomUser	Custom email-based user
Product.Product_Category	Product categories
Product.Product	Medicine/product information
Product.Product_Variant	Product size, price, stock and quantity
Cart.Carts	User shopping cart
Cart.CartItems	Products added to cart
Doctor.Doctor	Doctor profile
Doctor.Appointment	Appointment information
Order.Orders	Order information
Order.OrderItems	Products included in an order
Shipping.Shipping_addresses	Customer shipping information
Contact.FeedBack	Customer feedback
🚀 Getting Started
Prerequisites

Make sure the following are installed:

Python 3.9+
pip
Git
1. Clone the Repository
git clone https://github.com/nidhibisen24/Medifill.git
cd Medifill
2. Create a Virtual Environment
Windows PowerShell
python -m venv .venv
.venv\Scripts\Activate.ps1
macOS / Linux
python3 -m venv .venv
source .venv/bin/activate
3. Upgrade pip
python -m pip install --upgrade pip
4. Install Dependencies

The project currently does not include a requirements.txt file.

Install the required packages manually:

pip install django==4.2 pillow
5. Apply Database Migrations
python manage.py migrate

If you modify or add models:

python manage.py makemigrations
python manage.py migrate
6. Create an Admin User

To access the Django Admin Panel:

python manage.py createsuperuser

The project uses a custom email-based user model, so provide an email address when prompted.

7. Run the Development Server
python manage.py runserver

Open the application in your browser:

http://127.0.0.1:8000/
Django Admin
http://127.0.0.1:8000/admin/

Press Ctrl + C to stop the development server.

🌐 Main Application Routes
Feature	URL
Homepage	/
Login	/login/
Signup	/signup/
Logout	/logout/
Product Search	/Product/search/
Products	/Product/
Shopping Cart	/Cart/
Add to Cart	/Cart/add-to-cart/<id>/
Remove Cart Item	/Cart/remove-cart/<id>/
Doctors	/Doctor/
Shop Registration	/Shop/
Payment	/Payment/
Orders	/order/
Feedback	/Contact/
Django Admin	/admin/

Some URL patterns may vary depending on the URL configuration inside individual Django apps.

🖼️ Static & Media Files

Static assets are stored in:

static/

The project uses:

STATIC_URL = "/static/"

Uploaded media files are configured using:

MEDIA_URL = "/media/"
MEDIA_ROOT = os.path.join(BASE_DIR, "media")

For production, media files should be served using a web server or cloud/object storage solution.

📧 Email Configuration

The project includes SMTP configuration for password-reset functionality.

For production environments:

Do not hard-code email credentials.
Store credentials in environment variables.
Use an application-specific email password or transactional email provider.
Never commit secrets to GitHub.

Example environment variables:

EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USE_TLS=True
EMAIL_HOST_USER=your-email@example.com
EMAIL_HOST_PASSWORD=your-application-password
🔐 Security Considerations

The current configuration is intended for development.

Before deploying publicly:

Set DEBUG = False
Replace the development SECRET_KEY
Configure ALLOWED_HOSTS
Move email credentials to environment variables
Configure HTTPS
Configure secure cookies
Configure CSRF trusted origins
Use a production-ready database
Do not commit sensitive user data
Do not commit uploaded media
Validate form input server-side
Add proper authorization checks
Protect user-specific operations
Review payment processing before accepting real payments
Use a production WSGI/ASGI server
🧪 Testing

Run the Django test suite:

python manage.py test

Important areas for testing include:

User registration and login
Product search
Cart creation and management
Cart ownership
Cart total calculation
Doctor appointment creation
Shop-owner product insertion
Order creation
Payment status updates
Shipping address validation
Password reset
Email delivery
⚠️ Current Implementation Status

Some modules currently provide the foundation for future improvements.

Payment

The payment module currently prepares the payment page and calculates the unpaid cart total.

A complete third-party payment gateway integration is not currently implemented.

Checkout

Order models are available, but the complete cart-to-order checkout workflow can be further integrated.

Shipping

Shipping address models are implemented, while the complete shipping workflow can be extended.

Forms & Validation

Some views currently handle request parameters directly. These can be improved using Django Forms and stronger server-side validation.

Testing

The project contains test files in several applications, but automated test coverage can be expanded further.

🔮 Future Improvements
 Integrate Razorpay or Stripe payment gateway
 Complete cart-to-order checkout workflow
 Add order cancellation and refund handling
 Add email/SMS notifications
 Improve product filtering and sorting
 Add medicine availability tracking
 Add doctor availability and appointment scheduling
 Add shop-owner dashboard
 Add customer order dashboard
 Improve authorization and permissions
 Increase automated test coverage
 Add REST APIs using Django REST Framework
 Migrate to PostgreSQL for production
 Deploy using a production WSGI/ASGI server
 Improve responsive UI/UX
🧰 Useful Django Commands
Check project configuration
python manage.py check
Create migrations
python manage.py makemigrations
Apply migrations
python manage.py migrate
Create admin user
python manage.py createsuperuser
Run tests
python manage.py test
Open Django shell
python manage.py shell
Run development server
python manage.py runserver
Collect static files
python manage.py collectstatic
📌 Project Status

Status: Development / Academic Project

MediFill provides the core foundation for an online healthcare and medicine platform, including authentication, product management, cart functionality, doctor discovery, appointment booking, shop-owner functionality, orders, shipping and customer feedback.

Further development can extend the payment, checkout, authorization, testing and deployment capabilities.

👩‍💻 Repository

GitHub:
https://github.com/nidhibisen24/Medifill

📝 License

No license is currently specified for this project.

If you plan to distribute or reuse the project publicly, consider adding an appropriate open-source license.


**Bas pura upar wala ek hi block copy karo → `README.md` mein paste karo → save karo.** ❤️

Phir terminal mein sirf:

```powershell
git add README.md
git commit -m "Update README documentation"
git push
