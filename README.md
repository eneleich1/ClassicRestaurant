# ClassicRestaurant

ClassicRestaurant is a restaurant web application built as a learning and portfolio project using **React**, **ASP.NET Core Web API**, and **MySQL**.

The goal of this project is to practice a simple full-stack application with authentication, menu browsing, order creation, simulated payment, order status tracking, and a basic admin/staff dashboard.

## Project Purpose

This is a hypothetical restaurant system created for training purposes.

The project is intentionally simple. It is not meant to be a large production-level restaurant platform. The main purpose is to practice the most important parts of a real web application without making the project too complex.

## Technology Stack

### Frontend

- React
- React Router
- JavaScript or TypeScript
- HTML
- CSS

### Backend

- ASP.NET Core Web API
- JWT Authentication
- Role-based Authorization
- Entity Framework Core

### Database

- MySQL

## Main Features

### Guest User

A guest user can:

- Visit the landing page
- View restaurant information and photos
- Browse the menu
- Add items to the cart/order
- Continue to checkout as a guest
- Enter basic information before placing the order

### Registered Customer

A registered customer can:

- Register an account
- Log in
- See their username in the navigation bar
- Browse the menu
- Add dishes, appetizers, and drinks to the order
- Place an order
- Track the order status

### Admin / Staff User

An admin or staff user can:

- Access the admin dashboard
- View incoming orders
- See orders sorted by date and time
- Confirm paid orders
- Move orders through the preparation workflow
- Mark orders as ready
- Mark orders as delivered or completed

## Application Flow

1. The user enters the website.
2. The user can browse as a guest or log in/register.
3. The landing page shows restaurant information, photos, and navigation links.
4. The user opens the menu page.
5. The menu displays items by category:
   - Main dishes
   - Appetizers
   - Drinks
6. The user adds items to the cart/order.
7. The user reviews the order.
8. During checkout:
   - Guest users enter basic customer information.
   - Registered users continue with their account information.
9. Payment is simulated.
10. After payment, the order is created.
11. The order appears in the admin dashboard.
12. Staff updates the order status.
13. The customer can track the order status.
14. The order is completed when it is delivered or served.

## Order Types

The system supports three simple order types:

- Dine In
- Takeout
- Delivery

Depending on the order type, the user may provide:

- Table number
- Customer name
- Phone number
- Delivery address

## Order Statuses

The order workflow uses the following statuses:

```text
PendingPayment
Paid
Confirmed
InPreparation
Ready
Delivered
Completed
Cancelled
```

For the user interface, these statuses can be displayed in a simpler way, such as:

```text
Pending
Confirmed
In Process
Ready
Delivered
Completed
Cancelled
```

## Payment

Payment is simulated in this project.

The application does not store real credit card information. When the user completes checkout, the system marks the payment as completed for training purposes.

## Main Pages

### Landing Page

The landing page shows:

- Restaurant presentation
- Restaurant photos
- Basic information
- Navigation links
- Menu link
- Login and register links
- Current user status: Guest, Customer, Admin, or Staff

### Login Page

The login page allows registered users to log in.

The login request is sent to the ASP.NET Core backend. If the credentials are valid, the backend returns a JWT token.

### Register Page

The register page allows new customers to create an account.

### Menu Page

The menu page shows menu items organized by category:

- Main dishes
- Appetizers
- Drinks

Each menu item includes:

- Name
- Description
- Price
- Image
- Add to order button

### Cart / Order Page

The cart/order page shows the selected items before checkout.

The user can:

- Review selected items
- Change quantities
- Remove items
- Submit the order

### Checkout Page

The checkout page handles guest or registered customer checkout.

The project uses simulated payment.

### Order Status Page

The order status page allows the customer to see the current status of the order.

### Admin Dashboard

The admin dashboard allows admin or staff users to manage incoming orders.

Orders are shown by date and time.

Staff can update the order status using this workflow:

```text
Paid -> Confirmed -> InPreparation -> Ready -> Delivered -> Completed
```

## Database Tables

The basic database structure includes:

```text
Users
Roles
Categories
MenuItems
Orders
OrderItems
Payments
```

## Basic Entity Description

### Users

Stores registered users.

Main fields:

```text
Id
FullName
Email
PasswordHash
RoleId
CreatedAt
```

### Roles

Stores user roles.

Examples:

```text
Customer
Admin
Staff
```

### Categories

Stores menu categories.

Examples:

```text
Main Dishes
Appetizers
Drinks
```

### MenuItems

Stores restaurant menu items.

Main fields:

```text
Id
CategoryId
Name
Description
Price
ImageUrl
IsAvailable
```

### Orders

Stores customer orders.

Main fields:

```text
Id
OrderNumber
UserId
CustomerName
CustomerPhone
OrderType
TableNumber
DeliveryAddress
Status
CreatedAt
EstimatedReadyTime
```

### OrderItems

Stores the items inside each order.

Main fields:

```text
Id
OrderId
MenuItemId
Quantity
UnitPrice
```

### Payments

Stores simulated payment information.

Main fields:

```text
Id
OrderId
PaymentStatus
PaymentMethod
PaidAt
```

## Suggested API Endpoints

### Authentication

```text
POST /api/auth/register
POST /api/auth/login
```

### Menu

```text
GET /api/menu
GET /api/menu/categories
GET /api/menu/items
GET /api/menu/items/{id}
```

### Orders

```text
POST /api/orders
GET /api/orders/{id}
GET /api/orders/my-orders
```

### Admin / Staff Orders

```text
GET /api/admin/orders
PUT /api/admin/orders/{id}/status
```

## Suggested Frontend Structure

```text
src/
  components/
    Navbar.jsx
    MenuItemCard.jsx
    Cart.jsx
    OrderStatus.jsx
    AdminOrderTable.jsx

  pages/
    LandingPage.jsx
    LoginPage.jsx
    RegisterPage.jsx
    MenuPage.jsx
    CheckoutPage.jsx
    OrderStatusPage.jsx
    AdminDashboard.jsx

  services/
    api.js
    authService.js
    menuService.js
    orderService.js

  context/
    AuthContext.jsx
    CartContext.jsx
```

## Learning Goals

This project is meant to practice:

- React components
- React routing
- React state management
- API calls from frontend to backend
- ASP.NET Core controllers
- DTOs
- Services
- Entity Framework Core
- MySQL database relationships
- JWT authentication
- Role-based authorization
- CRUD operations
- Order workflow logic
- Basic dashboard development

## First Version Scope

The first version should stay simple and focus only on:

- Landing page
- Login and registration
- Guest browsing
- Menu by categories
- Cart/order creation
- Simulated checkout
- Order status tracking
- Admin dashboard for order management

## Future Improvements

These features are not part of the first version, but could be added later:

- Real payment provider integration
- Email confirmation
- SMS notification
- Reservation system
- Coupon system
- Inventory tracking
- Delivery tracking map
- Reports and analytics

## Project Status

Planned / In Development

## Author

Nestor Longa

## Project Type

Learning project / Portfolio project
