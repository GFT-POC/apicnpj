# Documentation: SupplierController.java

## Overview
The `SupplierController` class is a REST controller in a Spring Boot application that manages CRUD operations for `Supplier` entities. It provides endpoints for creating, retrieving, updating, and deleting suppliers. The controller interacts with the `SupplierService` to perform business logic and data manipulation.

## Class Details

### Package
```java
package com.example.supplier.controller;
```
The class is part of the `com.example.supplier.controller` package.

### Annotations
- `@RestController`: Indicates that this class is a REST controller, handling HTTP requests and returning JSON responses.
- `@RequestMapping("/api/suppliers")`: Maps all endpoints in this controller to the base URL `/api/suppliers`.

### Dependencies
- **SupplierService**: The service layer responsible for business logic and data operations. It is injected using `@Autowired`.

## Endpoints

### 1. Get All Suppliers
```java
@GetMapping
public List<Supplier> getAllSuppliers()
```
- **HTTP Method**: `GET`
- **URL**: `/api/suppliers`
- **Description**: Retrieves a list of all suppliers.
- **Response**: Returns a `List<Supplier>` containing all supplier entities.

---

### 2. Get Supplier by ID
```java
@GetMapping("/{id}")
public ResponseEntity<Supplier> getSupplierById(@PathVariable Long id)
```
- **HTTP Method**: `GET`
- **URL**: `/api/suppliers/{id}`
- **Description**: Retrieves a supplier by its unique ID.
- **Path Variable**: `id` (Long) - The ID of the supplier to retrieve.
- **Response**:
  - `200 OK`: Returns the supplier entity if found.
  - `404 Not Found`: If no supplier exists with the given ID.

---

### 3. Create Supplier
```java
@PostMapping
public Supplier createSupplier(@RequestBody Supplier supplier)
```
- **HTTP Method**: `POST`
- **URL**: `/api/suppliers`
- **Description**: Creates a new supplier entity.
- **Request Body**: `Supplier` - The supplier details to be created.
- **Response**: Returns the created `Supplier` entity.

---

### 4. Update Supplier
```java
@PutMapping("/{id}")
public ResponseEntity<Supplier> updateSupplier(@PathVariable Long id, @RequestBody Supplier supplierDetails)
```
- **HTTP Method**: `PUT`
- **URL**: `/api/suppliers/{id}`
- **Description**: Updates an existing supplier's details.
- **Path Variable**: `id` (Long) - The ID of the supplier to update.
- **Request Body**: `Supplier` - The updated supplier details.
- **Response**:
  - `200 OK`: Returns the updated supplier entity if successful.
  - `404 Not Found`: If no supplier exists with the given ID.

---

### 5. Delete Supplier
```java
@DeleteMapping("/{id}")
public ResponseEntity<Void> deleteSupplier(@PathVariable Long id)
```
- **HTTP Method**: `DELETE`
- **URL**: `/api/suppliers/{id}`
- **Description**: Deletes a supplier by its unique ID.
- **Path Variable**: `id` (Long) - The ID of the supplier to delete.
- **Response**:
  - `204 No Content`: If the supplier was successfully deleted.
  - `404 Not Found`: If no supplier exists with the given ID.

---

## Insights

### Key Features
- **CRUD Operations**: The controller provides full CRUD functionality for managing suppliers.
- **Response Handling**: Uses `ResponseEntity` to handle HTTP responses, ensuring proper status codes are returned.
- **Path Variables and Request Body**: Utilizes `@PathVariable` and `@RequestBody` annotations for dynamic URL parameters and JSON payloads.

### Dependencies
- **SupplierService**: Acts as the intermediary between the controller and the data layer, encapsulating business logic.
- **Supplier**: Represents the data model for suppliers.

### Error Handling
- The controller handles cases where a supplier is not found by returning `404 Not Found`.
- For deletion and updates, it ensures proper HTTP status codes are returned based on the operation's success.

### RESTful Design
The controller adheres to RESTful principles by using appropriate HTTP methods (`GET`, `POST`, `PUT`, `DELETE`) and meaningful status codes (`200`, `404`, `204`).

### Scalability
The design allows for easy extension of functionality, such as adding filters or pagination for the `getAllSuppliers` endpoint.
