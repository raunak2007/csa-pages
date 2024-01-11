---
layout: post
title: JQUERY & CRUD HACKS
description: hacks for CRUD with JQUERY
type: hacks
week: 15
categories: ['Javascript', 'Lesson', 'Tri 2']
tags: ['Notebook', 'Lesson', 'Javascript', 'jQuery']
---

### Real-Life Applications of jQuery:
1. **Dropdown Menus Animation:**
   - jQuery is used to make dropdown menus appear smoothly on web pages. This is a common user interface enhancement where, instead of a sudden appearance, dropdown menus can have a more visually appealing and smooth transition.

2. **AJAX Implementation:**
   - jQuery simplifies the implementation of AJAX (Asynchronous JavaScript and XML). It is used to update parts of a web page without requiring a full page reload. This allows for more dynamic and responsive web applications, as only specific portions of the page are updated with new data from the server.

### Free Response and MCQ:

1. **CRUD:**
   - CRUD stands for:
     - Create
     - Read
     - Update
     - Delete

2. **HTTP Verbs for CRUD Actions:**
   - The HTTP verbs associated with each CRUD action are:
     - Create (C): POST
     - Read (R): GET
     - Update (U): PUT
     - Delete (D): DELETE

3. **jQuery Definition:**
   - jQuery is described as a JavaScript library that simplifies HTML document manipulation, AJAX, and web development interaction. It provides a set of functions and utilities that make it easier to work with and manipulate HTML documents, handle events, and perform asynchronous requests.

4. **jQuery Event Handler for a Data Table:**
   - Matching A, B, and C into the jQuery event handler:
     ```javascript
     $(C).on(A, B, function() {
       // code
     });
     ```
     Here, A is the event type ('click'), B is the selector for the target element ('.delete-btn'), and C is the overall target element ('#data-table'). This event handler is set up to trigger a function when an element with the class '.delete-btn' inside the element with id 'data-table' is clicked.

5. **Use of jQuery with CRUD:**
   - jQuery is used with CRUD operations because it simplifies the process of performing Create, Read, Update, and Delete operations on data without writing extensive code. It facilitates easy interaction between the front end (using jQuery) and the back end, making it more efficient to handle data operations in web development.

# Finish the update JQUERY function
- its all the way at the end, you should see the green comment
- you can choose to use the two lines I've already given or not

<script src="https://code.jquery.com/jquery-3.6.4.min.js"></script>
<style>
  body {
    background-color: #ffe1f4; /* Barbie Pink */
    font-family: 'Arial', sans-serif;
    margin: 0;
    padding: 0;
  }
  table {
    border-collapse: collapse;
    width: 100%;
    margin-top: 20px;
  }
  th, td {
    border: 1px solid #e66b8f; /* Barbie Pink */
    padding: 10px;
    text-align: left;
  }
  th {
    background-color: #ff8bbd; /* Barbie Pink */
    color: white;
  }
  button {
    background-color: #ff8bbd; /* Barbie Pink */
    color: white;
    border: none;
    padding: 8px 12px;
    cursor: pointer;
  }
  button:hover {
    background-color: #e66b8f; /* Lighter Barbie Pink */
  }
</style>


<table id="data-table">
  <thead>
    <tr>
      <th>ID</th>
      <th>Name</th>
      <th>Email</th>
      <th>Actions</th>
    </tr>
  </thead>
  <tbody>
    <!-- Data will be dynamically added here -->
  </tbody>
</table>

<button id="create-btn">Create Barbie Character</button>

<script>
const initialData = [
  { id: 1, name: 'Barbie', email: 'barbie@example.com' },
  { id: 2, name: 'Ken', email: 'ken@example.com' }
];

function renderData(data) {
  const tableBody = $('#data-table tbody');
  tableBody.empty();

  data.forEach(item => {
    const row = `
      <tr>
        <td>${item.id}</td>
        <td>${item.name}</td>
        <td>${item.email}</td>
        <td>
          <button class="update-btn" data-id="${item.id}">Update</button>
          <button class="delete-btn" data-id="${item.id}">Delete</button>
        </td>
      </tr>
    `;
    tableBody.append(row);
  });
}

function createBarbieCharacter() {
  const newName = prompt('Enter the name of the Barbie character:');
  const newEmail = prompt('Enter the email of the Barbie character:');
  const newId = initialData.length + 1;
  
  const newData = [...initialData, { id: newId, name: newName, email: newEmail }];
  initialData.push({ id: newId, name: newName, email: newEmail });

  renderData(newData);
}

$('#create-btn').on('click', createBarbieCharacter);

$('#data-table').on('click', '.update-btn', function() {
  const idToEdit = $(this).data('id');
  const updateIndex = initialData.findIndex(item => item.id === idToEdit);

  // check user index exist
  if (updateIndex !== -1) {
    // new name and email input
    const updatedName = prompt('Enter the new name of the Barbie character:', initialData[updateIndex].name);
    const updatedEmail = prompt('Enter the new email of the Barbie character:', initialData[updateIndex].email);
    
    // provided name and email valid
    if (updatedName !== null && updatedEmail !== null) {
      // Update initialData array
      initialData[updateIndex].name = updatedName;
      initialData[updateIndex].email = updatedEmail;

      renderData(initialData);
    } else {
      alert('Please provide both name and email.');
    }
  } else {
    alert('Character not found.');
  }
});

$('#data-table').on('click', '.delete-btn', function() {
  const idToDelete = $(this).data('id');
  const newData = initialData.filter(item => item.id !== idToDelete);
  renderData(newData);
});

// Initial rendering
renderData(initialData);
</script>

# Explanation of Code:

### External Libraries
```html
<script src="https://code.jquery.com/jquery-3.6.4.min.js"></script>
```
This line imports the jQuery library, a powerful tool for simplifying JavaScript code and working with the Document Object Model (DOM) in a concise and efficient manner.

### Styling
```html
<style>
  /* CSS styling for the page */
</style>
```
This section contains inline CSS styles that define the visual aspects of the HTML elements. jQuery doesn't directly handle styling but works seamlessly with the DOM, which includes styling.

### HTML Table Structure
```html
<table id="data-table">
  <!-- Table header -->
  <thead>
    <tr>
      <th>ID</th>
      <th>Name</th>
      <th>Email</th>
      <th>Actions</th>
    </tr>
  </thead>
  <!-- Table body (data will be dynamically added here) -->
  <tbody>
    <!-- Data will be dynamically added here -->
  </tbody>
</table>
```
Here, the HTML table is the structure that jQuery will interact with. It will dynamically add and manipulate data within this table.

### Create Button
```html
<button id="create-btn">Create Barbie Character</button>
```
This button, with the ID "create-btn," will be selected and manipulated using jQuery to trigger the creation of a new Barbie character.

### jQuery Section
```html
<script>
  // JavaScript code using jQuery
</script>
```
This section contains jQuery code that simplifies DOM manipulation and event handling.

#### Data Initialization
```javascript
const initialData = [
  { id: 1, name: 'Barbie', email: 'barbie@example.com' },
  { id: 2, name: 'Ken', email: 'ken@example.com' }
];
```
This array, `initialData`, is the initial set of Barbie character data that jQuery will interact with.

#### Rendering Function
```javascript
function renderData(data) {
  const tableBody = $('#data-table tbody');
  tableBody.empty();

  // Dynamically render data into the table using jQuery
  data.forEach(item => {
    const row = `
      <tr>
        <td>${item.id}</td>
        <td>${item.name}</td>
        <td>${item.email}</td>
        <td>
          <button class="update-btn" data-id="${item.id}">Update</button>
          <button class="delete-btn" data-id="${item.id}">Delete</button>
        </td>
      </tr>
    `;
    tableBody.append(row);
  });
}
```
jQuery simplifies the selection and manipulation of DOM elements. In this case, it selects the table body and dynamically populates it with rows based on the provided data.

#### Create Barbie Character Function
```javascript
function createBarbieCharacter() {
  // Function using jQuery to prompt the user and update the table
}
```
This function, triggered by the "Create Barbie Character" button, uses jQuery to prompt the user for input and dynamically updates the table with the new character data.

#### Event Handlers
```javascript
$('#create-btn').on('click', createBarbieCharacter);
$('#data-table').on('click', '.update-btn', function() { /* ... */ });
$('#data-table').on('click', '.delete-btn', function() { /* ... */ });
```
jQuery event handlers are employed here. The first line associates a click event with the "Create Barbie Character" button, while the next two lines handle click events on the update and delete buttons within the data table.

#### Update and Delete Functions
```javascript
// Functions using jQuery to update and delete Barbie characters
```

#### Initial Rendering
```javascript
// Initial rendering of data using jQuery
renderData(initialData);
</script>
```
The script concludes with the initial rendering of the table using jQuery to display the initial set of Barbie character data.

In summary, this code leverages jQuery to streamline the manipulation of the DOM, making it easier to create, update, and delete Barbie character data on the web page. The code showcases jQuery's power in handling events, selecting elements, and dynamically updating the HTML content.
