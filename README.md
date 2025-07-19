# Inventory-Management-UI
Inventory Management UI

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Inventory Management</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f4f4f4;
      padding: 30px;
    }

    h1 {
      text-align: center;
      color: #333;
    }

    .container {
      max-width: 900px;
      margin: auto;
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    form {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      margin-bottom: 20px;
    }

    input[type="text"], input[type="number"] {
      flex: 1;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 6px;
    }

    button {
      padding: 10px 20px;
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }

    .add-btn {
      background-color: #28a745;
      color: white;
    }

    .edit-btn {
      background-color: #ffc107;
      color: white;
    }

    .delete-btn {
      background-color: #dc3545;
      color: white;
    }

    table {
      width: 100%;
      border-collapse: collapse;
    }

    th, td {
      padding: 12px;
      border-bottom: 1px solid #ddd;
      text-align: center;
    }

    th {
      background-color: #007bff;
      color: white;
    }

    @media (max-width: 600px) {
      form {
        flex-direction: column;
      }
    }
  </style>
</head>
<body>

  <h1>Inventory Management UI</h1>
  <div class="container">
    <form id="inventory-form">
      <input type="text" id="item-name" placeholder="Item Name" required>
      <input type="number" id="item-quantity" placeholder="Quantity" required>
      <input type="text" id="item-category" placeholder="Category" required>
      <button type="submit" class="add-btn">Add Item</button>
    </form>

    <table>
      <thead>
        <tr>
          <th>Item Name</th>
          <th>Quantity</th>
          <th>Category</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody id="inventory-table-body"></tbody>
    </table>
  </div>

  <script>
    const form = document.getElementById('inventory-form');
    const nameInput = document.getElementById('item-name');
    const quantityInput = document.getElementById('item-quantity');
    const categoryInput = document.getElementById('item-category');
    const tableBody = document.getElementById('inventory-table-body');

    let inventory = [];
    let editIndex = -1;

    form.addEventListener('submit', function(e) {
      e.preventDefault();
      const name = nameInput.value.trim();
      const quantity = quantityInput.value.trim();
      const category = categoryInput.value.trim();

      if (name === '' || quantity === '' || category === '') return;

      const newItem = { name, quantity, category };

      if (editIndex === -1) {
        inventory.push(newItem);
      } else {
        inventory[editIndex] = newItem;
        editIndex = -1;
        form.querySelector('button').textContent = "Add Item";
        form.querySelector('button').classList.remove('edit-btn');
        form.querySelector('button').classList.add('add-btn');
      }

      renderTable();
      form.reset();
    });

    function renderTable() {
      tableBody.innerHTML = "";
      inventory.forEach((item, index) => {
        const row = document.createElement('tr');

        row.innerHTML = `
          <td>${item.name}</td>
          <td>${item.quantity}</td>
          <td>${item.category}</td>
          <td>
            <button class="edit-btn" onclick="editItem(${index})">Edit</button>
            <button class="delete-btn" onclick="deleteItem(${index})">Delete</button>
          </td>
        `;
        tableBody.appendChild(row);
      });
    }

    window.editItem = function(index) {
      const item = inventory[index];
      nameInput.value = item.name;
      quantityInput.value = item.quantity;
      categoryInput.value = item.category;
      editIndex = index;

      form.querySelector('button').textContent = "Update Item";
      form.querySelector('button').classList.remove('add-btn');
      form.querySelector('button').classList.add('edit-btn');
    }

    window.deleteItem = function(index) {
      inventory.splice(index, 1);
      renderTable();
    }
  </script>

</body>
</html>

