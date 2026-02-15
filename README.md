# Tint Clothing POS (Web)

A comprehensive, web-based Point of Sale (POS) system designed for Tint Clothing. This application streamlines retail operations including billing, inventory management, sales tracking, and return/exchange processing.

## 🚀 Key Features

### 🛒 Point of Sale (POS) & Billing
-   **Efficient Billing:** Fast item lookup and addition to cart.
-   **Stock Management:** Real-time stock validation to prevent overselling.
-   **Flexible Payments:** Supports Cash, Online (UPI/Card), and **Split Payments** (part Cash, part Online).
-   **Receipt Printing:** Generates professional, printable receipts with customer and payment details.

### 📦 Inventory Management
-   **CRUD Operations:** Easily Add, Edit, and Delete inventory items.
-   **Real-time Updates:** Stock levels automatically adjust upon sales or returns.
-   **Search:** Quick filtering of items by name or category.

### 🔄 Returns & Exchanges
-   **Bill Lookup:** Retrieve past sales using Bill Number.
-   **Seamless Processing:** Select specific items to return; the system automatically calculates the balance and updates the cart for exchanges.
-   **Stock Adjustment:** Returned items are automatically added back to inventory.

### 📊 Sales Analytics
-   **Dashboard:** Visual insights into business performance.
-   **Charts:**
    -   **Revenue Trends:** Daily/Weekly/Monthly sales graphs.
    -   **Category Analysis:** Breakdown of sales by product category.
    -   **Top Products:** Identification of best-selling items.
-   **Filters:** View data by Today, Last Week, Last Month, or Custom Date Ranges.

### 🔒 Security
-   **Authentication:** Google Sign-In integration.
-   **Role-Based Access:** Secured via Firebase Firestore Rules. Only authorized emails in the `admins` collection can access the system.

## 🛠️ Tech Stack

-   **Frontend:** HTML5, CSS3, JavaScript (ES6 Modules)
-   **Backend:** Firebase Firestore (Realtime Database)
-   **Auth:** Firebase Authentication
-   **Hosting:** Firebase Hosting
-   **Libraries:**
    -   [Chart.js](https://www.chartjs.org/) (Analytics)
    -   [Google Fonts](https://fonts.google.com/) (Inter & Outfit)

## ⚙️ Setup & Installation

### Prerequisites
-   Node.js & npm installed
-   Firebase CLI (`npm install -g firebase-tools`)

### Installation
1.  **Clone the Repository**
    ```bash
    git clone <repository-url>
    cd project_tint
    ```

2.  **Firebase Setup**
    -   Create a new project in the [Firebase Console](https://console.firebase.google.com/).
    -   Enable **Authentication** (Google Sign-In).
    -   Enable **Cloud Firestore** in test/production mode.
    -   Update `public/assets/js/firebase-config.js` with your project's configuration keys.

3.  **Access Control**
    -   Go to your Firestore Database.
    -   Create a collection named `admins`.
    -   Add a document where the **Document ID** is the email address of the authorized admin (e.g., `admin@example.com`).

4.  **Run Locally**
    ```bash
    firebase serve
    ```
    Access the app at `http://localhost:5000`.

5.  **Deploy**
    ```bash
    firebase deploy
    ```

## 📂 Project Structure

```
project_tint/
├── public/                 # Hosting Root
│   ├── assets/
│   │   ├── css/            # Stylesheets
│   │   ├── js/             # Application Logic
│   │   │   ├── app.js      # Core Logic (POS, Inventory, Sales)
│   │   │   ├── auth-guard.js # Auth Protection
│   │   │   └── firebase-config.js
│   │   └── images/
│   ├── index.html          # POS / Billing Page
│   ├── inventory.html      # Inventory Management
│   ├── sales.html          # Sales History & Analytics
│   ├── exchange.html       # Return & Exchange
│   └── login.html          # Login Page
├── firebase.json           # Firebase Hosting Config
└── firestore.rules         # Database Security Rules
```

## 🛡️ Security Rules

The application uses strict Firestore rules ensuring only verified admins can read/write data.

```javascript
match /admins/{email} {
  allow read: if request.auth != null;
  allow write: if isAdmin();
}
```

## 🤝 Contributing

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request
