# E-commerce Application  

This is a simple e-commerce application built using Python, Flask, SQLite, and vanilla JavaScript. The application demonstrates basic functionalities such as listing products, placing orders, and viewing order details.  

## Features  

- View a list of products with their details (name, price, description, and image).  
- Place an order for a product.  
- View a list of orders, including details such as product name, quantity, total price, and status.  
- Sample products pre-loaded into the database.  

## Project Structure  

```
ecommerce-app/  
├── static/  
│   ├── css/  
│   │   └── style.css  
│   ├── js/  
│   │   ├── main.js  
│   │   └── orders.js  
│   └── images/  
├── templates/  
│   ├── index.html  
│   └── orders.html  
├── database/  
│   └── (SQLite database will be created here)  
├── app.py  
└── README.md  
```  

## Getting Started  

### Prerequisites  

- Python 3.x installed  
- `pip` (Python package installer) installed  

### Installation  

1. Clone the repository or copy the script to your local machine.  
2. Navigate to the project directory:  
   ```bash  
   cd ecommerce-app  
   ```  
3. Create and activate a virtual environment (optional but recommended):  
   ```bash  
   python3 -m venv venv  
   source venv/bin/activate  # On Windows, use venv\Scripts\activate  
   ```  
4. Install required dependencies:  
   ```bash  
   pip install flask  
   ```  

### Running the Application  

1. Initialize the database:  
   The database will be created automatically with sample products when you run the app for the first time.  
2. Run the Flask application:  
   ```bash  
   python app.py  
   ```  
3. Open a browser and go to `http://127.0.0.1:5000` to access the application.  

## API Endpoints  

### Products  

- `GET /api/products`  
  Retrieves a list of all products.  

### Orders  

- `POST /api/orders`  
  Creates a new order.  
  - Request Body (JSON):  
    ```json  
    {  
      "product_id": 1,  
      "quantity": 1  
    }  
    ```  

- `GET /api/orders`  
  Retrieves a list of all orders.   

## Customization  

1. **Adding Products**  
   You can add new products directly to the `products` table in the SQLite database.  

2. **CSS Styles**  
   Modify `static/css/style.css` to customize the appearance of the application.  

3. **Static Files**  
   Add your images to the `static/images/` directory and update the database with the correct image URLs.  

## License  

This project is open-source and free to use.  

---  

Enjoy building and exploring this e-commerce application!  
