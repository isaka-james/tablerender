# TableRender

**TableRender** is a lightweight, customizable JavaScript library for rendering dynamic tables with search, pagination, and custom actions like edit and delete. This library is designed to be flexible, allowing developers to integrate table functionalities into their web applications with ease. 

The styles and functionality can be customized via external CSS and configuration options, making it suitable for a wide range of use cases.

## Features

- **Dynamic Table Rendering**: Automatically generates a table from a dataset.
- **Search Functionality**: Filter table data using a search bar.
- **Pagination**: Manage large datasets with easy-to-navigate pagination.
- **Customizable**: Pass custom class names for styling the table, rows, and cells.
- **Edit & Delete Actions**: Easily add edit and delete buttons to each row with customizable action handling.
- **Modal Popups**: Supports custom modal popups for editing and confirming deletion of data.

## Getting Started

### Installation

1. **Clone the Repository**

   ```bash
   git clone https://github.com/isaka-james/tablerender.git
   cd tablerender
   ```

2. **Include the CSS and JavaScript Files**

   Add the following lines to your HTML file to include TableRender:

   ```html
   <link rel="stylesheet" href="https://raw.githubusercontent.com/isaka-james/tablerender/main/tablerender.min.css">
   <script src="https://raw.githubusercontent.com/isaka-james/tablerender/main/tablerender.min.js"></script>
   ```

### Usage

1. **Prepare Your Data**

   Define your dataset as an array of objects. Each object represents a row in your table:

   ```javascript
   const data = [
       { id: 1, name: 'John Doe', age: 30, email: 'john@example.com' },
       { id: 2, name: 'Jane Smith', age: 25, email: 'jane@example.com' },
       // Additional rows...
   ];
   ```

2. **HTML Structure**

   Create the basic HTML structure for your table container, search bar, and pagination:

   ```html
   <input type="text" id="table-render-search" placeholder="Search...">
   <div id="table-container"></div>
   ```

3. **Initialize TableRender**

   Initialize the table by passing your data and configuration options:

   ```javascript
   const renderer = new TableRenderer(data, {
       tableId: 'table-container',
       searchId: 'table-render-search',
       rowsPerPage: 10,
       columns: ['id', 'name', 'age', 'email'], // Specify columns if needed
       customClasses: {
           table: 'custom-table-class',
           row: 'custom-row-class',
           cell: 'custom-cell-class'
       },
       enableEdit: true, // Enables the edit button
       enableDelete: true // Enables the delete button
   });

   renderer.createTable();
   ```

### Customization

- **Custom Class Names**

  Pass your custom class names for the table, rows, and cells via the `customClasses` option:

  ```javascript
  customClasses: {
      table: 'custom-table-class',
      row: 'custom-row-class',
      cell: 'custom-cell-class'
  }
  ```

- **Edit & Delete Buttons**

  To enable and customize edit and delete actions, set `enableEdit` and `enableDelete` to `true`. TableRender will generate buttons for each row:

  ```javascript
  enableEdit: true,
  enableDelete: true
  ```

- **Custom Modal Popups**

  TableRender supports custom modal popups for editing rows and confirming deletions. The modals can be styled and connected to your backend to handle updates and deletions.

  Example HTML for the modals:
  
  ```html
  <div id="edit-modal" class="modal">
      <form id="edit-form">
          <label for="name">Name</label>
          <input type="text" id="edit-name" name="name">
          <label for="age">Age</label>
          <input type="number" id="edit-age" name="age">
          <label for="email">Email</label>
          <input type="email" id="edit-email" name="email">
          <button type="submit">Update</button>
      </form>
  </div>

  <div id="delete-modal" class="modal">
      <p>Are you sure you want to delete this row?</p>
      <button id="confirm-delete">Yes, Delete</button>
      <button id="cancel-delete">Cancel</button>
  </div>
  ```

## Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="tablerender.min.css">
    <title>TableRender Example</title>
</head>
<body>

<input type="text" id="table-render-search" placeholder="Search...">
<div id="table-container"></div>

<script src="tablerender.min.js"></script>
<script>
    const data = [
        { id: 1, name: 'John Doe', age: 30, email: 'john@example.com' },
        { id: 2, name: 'Jane Smith', age: 25, email: 'jane@example.com' },
        // Additional rows...
    ];

    const renderer = new TableRenderer(data, {
        tableId: 'table-container',
        searchId: 'table-render-search',
        rowsPerPage: 10,
        columns: ['id', 'name', 'age', 'email'],
        enableEdit: true,
        enableDelete: true
    });

    renderer.createTable();
</script>

</body>
</html>
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
