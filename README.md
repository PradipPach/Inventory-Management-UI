# Inventory-Management-UI
Inventory Management UI
Discription :
This is a simple web-based inventory management system where users can add, edit, and delete items (like product name, quantity, and category). It uses HTML for structure, CSS for styling, and JavaScript for functionality — all in the frontend only (no backend).

Code Explanation :
HTML – Structure of the Page
Defines layout: headings, form inputs, buttons, and table.

Example:

html
Copy
Edit
<form>...</form>  <!-- Form for input -->
<table>...</table> <!-- Table to display inventory -->
Why: To structure the UI for user interaction.

 CSS – Styling and Design
Makes the UI user-friendly and responsive.

Styles buttons, layout, colors, spacing, etc.

Example:

css
Copy
Edit
.add-btn {
  background-color: #28a745;
}
Why: To make the UI look professional and usable.

 JavaScript :–
 Functionality and Logic
Handles user actions (add/edit/delete).

Dynamically updates the table without reloading the page.

Example:

js
Copy
Edit
form.addEventListener('submit', function(e) { ... });
Why: To manage dynamic behavior like form submission and UI updates.

Use:
Useful for retail, warehouse, or e-commerce dashboards.

Frontend mock for tools like Amazon Seller, Zoho Inventory, etc.

Run  project :
using linux:
1.sudo yum install httpd -y
2.sudo systemctl start httpd
3.sudo systemctl enable httpd
4.cd /var
5.cd www/html
6.sudo touch index.html
7.sudo nano index.html(code)
8.open ec2 copy public ip and paste browser then show outpt

