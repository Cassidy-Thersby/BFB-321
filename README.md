# FoodConnect
Connecting food suppliers with organizations that serve people in need.

## Project Purpose
The purpose of FoodConnect is to address the inefficiencies in South Africa’s food supply chain, particularly in the retail and agricultural sectors where food surplus is wasted while underserved communities face food insecurity. The digital platform is designed using Visual Studios and MySQL to connect food suppliers including farmers, shops, bakeries, and restaurants with recipient organisations such as underprivileged schools, shelters and non-governmental organisations. 
FoodConnect aims to improve inventory management and customer fulfilment by providing real-time visibility of surplus stock and streamlined communication between suppliers and recipients. This reduces the need for manual processes such as phone calls and emails, ensuring surplus food reaches those in need efficiently. 
The platform contributes to a social, economic and environmental sustainability for South Africa. Socially, it improves access to food in the underserved communities by improving redistribution. To reduce food insecurity. Economically, it reduces waste disposal costs for suppliers. Environmentally, less food is wasted therefore less resources are needed to produce more food. 
FoodConnect aims to create a more connected and sustainable food supply chain. With the use of technology, businesses are given the platform to operate more efficiently and in a more sustainable manner, having a positive social impact for South Africa. Through FoodConnect, surplus food is used as a resource instead of becoming waste. 


## Features !!!!

- **Dashboard**: Overview of inventory statistics and recent activity
- **Product Management**: Add, view, and update product information
- **Stock Tracking**: Update stock levels with detailed history
- **Vendor Management**: Login and registration system for vendors
- **Category Management**: Organize products by categories


## Database Setup
### Using SQLite Command Line

1. Open command prompt/terminal in the project directory
2. Run the SQL commands:
   ```bash
   sqlite3 foodconnect.db < foodconnect.sql
   ```

## Database Schema

### Entity Relationship Diagram (ERD)

```mermaid
erDiagram
    suppliers {
        INTEGER supplier_id PK
        TEXT supplier_name
        TEXT occupation
        TEXT location
        TEXT contact_number
        TEXT email
        TEXT password
        DATETIME created_at
    }

    recipients {
        INTEGER recipient_id PK
        TEXT recipient_name
        TEXT location
        TEXT contact_number
        TEXT email
        TEXT password
        DATETIME created_at
    }

    food_surplus {
        INTEGER surplus_id PK
        INTEGER supplier_id FK
        TEXT product_type
        TEXT description
        INTEGER quantity
        TEXT unit
        DATE expiry_date
        INTEGER min_stock_level
        INTEGER max_stock_level
        TEXT storage_condition
        TEXT notes
        DATETIME created_at
    }

  food_requests {
        INTEGER request_id PK
        INTEGER recipient_id FK
        TEXT food_type
        TEXT description
        INTEGER quantity_needed
        TEXT urgency
        DATE preferred_date
        TEXT notes
        DATETIME created_at
    }

    suppliers || -- o{ food_surplus : "provides"
    recipients || -- o{ food_requests : "submits"
    
```
## Database Demonstration
The foodconnect.sql migration file was executed successfully in SQLite to create and populate the foodconnect.db database.
It includes four normalized tables (suppliers, recipients, food_surplus, and food_requests) linked by foreign keys.
Sample data was inserted into each table (5 records per table) to demonstrate supplier-to-recipient food supply chain interactions.
The successful execution was verified using SELECT COUNT(*) queries, confirming that all tables contain sample data.


The database includes the following tables and views:

### Tables

1. **suppliers**: Registered food suppliers and their information
2. **recipients**: Registered recipients in need of food and their information
3. **food_surplus**: Available food product type, description, quantity with supplier name, location and contact information.
4. **food_requests** 

### Views !!!

1. **low_stock_products**: View of products with low stock alerts
2. **inventory_summary**: Summary statistics for the dashboard

## Sample Data !!!

The database includes sample data for testing:

- **9 Categories**: Electronics, Clothing, Books, Food & Beverages, Tools & Hardware, Furniture, Beauty & Health, Sports & Outdoors, Other
- **1 Vendor**: John Doe (TechStore Solutions)
- **10 Products**: Various items across different categories with realistic pricing and quantities
- **8 Stock Updates**: Sample transaction history

## File Structure

```
├── about.html                    # About us information page
├── index.html                    # Main dashboard
├── recipient-dashboard.html      # Main recipient dashboard
├── recipientlogin.html           # Recipient login page
├── signup.html                   # Sign up page
├── supplier-dashboard.html       # Main supplier dashboard
├── supplierlogin.html            # Recipient login page
├── uploadfoodsurplus.html        # Upload available surplus food
├── uploadrequest.html            # Request surplus food
├── view-available-surplus.html   # View available surplus inventory
├── view-recipient-needs.html     # View recipient food needs
└── readme.md                     # Explanation of project purpose, database schema and ERD. 
```

## Usage

1. Initialize the database using the SQLite command line method above
2. Open `index.html` in your web browser
3. Navigate through the different pages to request or upload available surplus food. 

## Technologies Used !!!

- **HTML5**: Structure and forms
- **Bootstrap 5.3.8**: UI framework and styling
- **Bootstrap Icons**: Icon set
- **SQLite**: Database for data persistence

## Browser Compatibility

The application works with all modern browsers that support HTML5 and CSS3, including:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

Note: This is a static HTML application. For production use, you would need to add backend functionality for database connectivity and form processing.
