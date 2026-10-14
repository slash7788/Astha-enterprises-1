# Aastha Enterprises — Online Mattress Selling System

Plain HTML + CSS + JavaScript frontend with a PHP 8 + MySQL backend.

## Structure
```
index.html              page shell
assets/css/style.css    design system and styles
assets/js/app.js        storefront, cart, checkout, account, admin UI
api/config.php          database settings (edit this)
api/db.php              shared helpers, sessions, auth guards
api/products.php        list products; admin add / stock / delete
api/auth.php            register, login, logout, me
api/orders.php          place order (server-side price + stock checks), order history
api/admin.php           dashboard stats, orders, customers, order status
api/contact.php         contact form and newsletter
database/schema.sql     tables + 8 sample products
database/create_admin.php  creates the admin login
```

## Setup (XAMPP / WAMP / any Apache + PHP 8 + MySQL)
1. Copy the folder to `htdocs/aastha-enterprises`.
2. Start Apache and MySQL, open phpMyAdmin, and import `database/schema.sql`.
3. Edit `api/config.php` if your MySQL user/password differ.
4. Create the admin: `php database/create_admin.php you@example.com "StrongPassword" "Your Name"`
5. Open http://localhost/aastha-enterprises/ — sign in with the admin account, then open **Admin**.

## Notes
- Passwords are hashed with `password_hash`; sessions are HTTP-only cookies; all SQL uses prepared statements.
- Prices and stock are always re-checked on the server when an order is placed.
- No payment gateway is integrated. Checkout offers Cash on Delivery / pay-later only, and payment status is set by the admin.
- Sample products and prices are placeholders. Add your real phone, email and address in `index.html` and `assets/js/app.js`.
- Product photos: put files in `assets/img/` and enter the path in "Image URL" when adding a product.
- For production use HTTPS and consider CSRF tokens, rate limiting and email order notifications.
