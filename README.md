# Scripts Repository  

Welcome to the **Scripts Repository**! This repository contains useful Python, shell scripts, and a basic e-commerce application for monitoring, security, and web development purposes.  

## Table of Contents  
- [About the Repository](#about-the-repository)  
- [Scripts](#scripts)  
  - [Python Scripts](#python-scripts)  
  - [Shell Scripts](#shell-scripts)  
  - [E-commerce Script](#e-commerce-script)  
- [How to Use](#how-to-use)  
- [License](#license)  

---  

## About the Repository  

This repository is designed to host practical scripts for system administration, monitoring, and basic web development. Each script or application is organized into its respective folder for ease of access.  

---  

## Scripts  

### Python Scripts  
The Python scripts can be found in the `python_scripts` folder:  
- **Nginx Access Log Monitoring Script**:  
  - Monitors Nginx access logs for repeated failed attempts.  
  - Automatically blocks malicious IP addresses using `iptables`.  

For more details about this script, visit the [Python Scripts.](python_scripts/readme.md).  

---  

### Shell Scripts  
The Shell scripts can be found in the `shell_scripts` folder:  
- **Resource Monitoring Script**:  
  - Monitors CPU, memory, and disk usage.  
  - Sends email alerts if usage exceeds predefined thresholds.  

For more details about this script, visit the [Shell Script.](shell_scripts/vm_monitoring).  

---  

### E-commerce Script  
The E-commerce application can be found in the `ecommerce-app` folder:  
- **E-commerce Application**:  
  - A simple web application to list products, place orders, and view order details.  
  - Built with Python, Flask, SQLite, and vanilla JavaScript.  

#### Features:  
- Product listing with name, price, description, and image.  
- Place orders with product quantity.  
- View all orders with details like product name, total price, and order status.  

#### How to Get Started:  
Visit the [E-commerce Script.](shell_scripts/Ecommerce_app) for detailed instructions on running the application.  

---  

## How to Use  

### Cloning the Repository  
To get started, clone this repository:  
```bash  
git clone https://github.com/Prasad-b-git/scripts.git  
cd scripts  
