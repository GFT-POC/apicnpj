# SupplierService Documentation

## Overview
The `SupplierService` class is a service layer in a Spring-based application that manages operations related to suppliers. It interacts with the `SupplierRepository` to perform CRUD (Create, Read, Update, Delete) operations and includes validation logic for supplier data, such as verifying the validity of a CNPJ (Brazilian company registration number).

---

## Class Details

### Package
`com.example.supplier.service`

### Dependencies
The class relies on the following components:
- **`SupplierRepository`**: Handles database operations for the `Supplier` entity.
- **`CodigoUtil`**: Provides utility methods, such as validating CNPJ values.
- **Spring Framework**: Utilizes annotations like `@Service` and `@Autowired` for dependency injection and service definition.

---

## Methods

### `createSupplier(Supplier supplier)`
Creates a new supplier in the system after validating the CNPJ.

#### Parameters:
- `supplier`: An instance of the `Supplier` entity containing supplier details.

#### Returns:
- The saved `Supplier` object.

#### Exceptions:
- Throws `IllegalArgumentException` if the CNPJ is invalid.

---

### `getAllSuppliers()`
Retrieves all suppliers from the database.

#### Returns:
- A `List<Supplier>` containing all suppliers.

---

### `getSupplierById(Long id)`
Fetches a supplier by its unique identifier.

#### Parameters:
- `id`: The ID of the supplier to retrieve.

#### Returns:
- An `Optional<Supplier>` containing the supplier if found, or empty if not.

---

### `updateSupplier(Long id, Supplier supplierDetails)`
Updates the details of an existing supplier.

#### Parameters:
- `id`: The ID of the supplier to update.
- `supplierDetails`: An instance of `Supplier` containing updated information.

#### Returns:
- The updated `Supplier` object.

#### Exceptions:
- Throws `IllegalArgumentException` if the CNPJ is invalid.
- Throws `RuntimeException` if the supplier with the given ID is not found.

---

### `deleteSupplier(Long id)`
Deletes a supplier by its unique identifier.

#### Parameters:
- `id`: The ID of the supplier to delete.

#### Returns:
- `true` if the supplier was successfully deleted.

#### Exceptions:
- Throws `RuntimeException` if the supplier with the given ID is not found.

---

## Insights

### Validation
The class uses `CodigoUtil.isValidCNPJ()` to ensure that the CNPJ provided for a supplier is valid. This adds a layer of data integrity to the application.

### Exception Handling
The service throws specific exceptions (`IllegalArgumentException` and `RuntimeException`) to handle invalid input and missing entities, ensuring robust error handling.

### Dependency Injection
The `@Autowired` annotation is used to inject the `SupplierRepository` dependency, following Spring's dependency injection principles.

### CRUD Operations
The class provides full CRUD functionality:
- **Create**: `createSupplier`
- **Read**: `getAllSuppliers`, `getSupplierById`
- **Update**: `updateSupplier`
- **Delete**: `deleteSupplier`

### Entity Interaction
The service interacts with the `Supplier` entity, which likely includes fields such as `nome`, `cnpj`, `nomeContato`, `emailContato`, and `telefoneContato`.

### Utility Integration
The use of `CodigoUtil` for CNPJ validation demonstrates modular design and separation of concerns.

---

## Annotations Used

| Annotation      | Purpose                                                                 |
|------------------|-------------------------------------------------------------------------|
| `@Service`       | Marks the class as a Spring service component.                        |
| `@Autowired`     | Enables automatic dependency injection for the `SupplierRepository`.  |

---

## Potential Enhancements
- **Custom Exceptions**: Replace `RuntimeException` with custom exceptions for better error semantics.
- **Pagination**: Add pagination support to `getAllSuppliers` for handling large datasets.
- **Logging**: Integrate logging to track operations and exceptions for debugging and monitoring.
