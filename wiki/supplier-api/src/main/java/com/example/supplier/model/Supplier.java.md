# Supplier.java Documentation

## Overview
The `Supplier` class represents a data structure for managing supplier information in a system. It is annotated as a JPA entity, enabling it to be persisted in a relational database. This class includes fields for supplier identification, contact details, and business information.

## Metadata
- **File Name**: `Supplier.java`
- **Package**: `com.example.supplier.model`

## Annotations
The class uses the following annotations:
- `@Entity`: Marks the class as a JPA entity, making it eligible for persistence.
- `@Id`: Specifies the primary key of the entity.
- `@GeneratedValue(strategy = GenerationType.IDENTITY)`: Indicates that the primary key value is auto-generated using the identity strategy.

## Fields
| Field Name       | Type       | Description                                                                 |
|------------------|------------|-----------------------------------------------------------------------------|
| `id`             | `Long`     | Unique identifier for the supplier.                                        |
| `nome`           | `String`   | Name of the supplier.                                                      |
| `cnpj`           | `long`     | Brazilian company registration number (CNPJ).                              |
| `nomeContato`    | `String`   | Name of the contact person for the supplier.                               |
| `emailContato`   | `String`   | Email address of the contact person.                                       |
| `telefoneContato`| `String`   | Phone number of the contact person.                                        |

## Methods
The class provides getter and setter methods for all fields, enabling encapsulation and controlled access to the data.

| Method Name            | Return Type | Description                                                                 |
|------------------------|-------------|-----------------------------------------------------------------------------|
| `getId()`              | `Long`      | Retrieves the supplier's unique identifier.                                |
| `setId(Long id)`       | `void`      | Sets the supplier's unique identifier.                                     |
| `getNome()`            | `String`    | Retrieves the name of the supplier.                                        |
| `setNome(String nome)` | `void`      | Sets the name of the supplier.                                             |
| `getCnpj()`            | `long`      | Retrieves the supplier's CNPJ.                                             |
| `setCnpj(long cnpj)`   | `void`      | Sets the supplier's CNPJ.                                                  |
| `getNomeContato()`     | `String`    | Retrieves the name of the contact person.                                  |
| `setNomeContato(String nomeContato)` | `void` | Sets the name of the contact person.                                       |
| `getEmailContato()`    | `String`    | Retrieves the email address of the contact person.                         |
| `setEmailContato(String emailContato)` | `void` | Sets the email address of the contact person.                              |
| `getTelefoneContato()` | `String`    | Retrieves the phone number of the contact person.                          |
| `setTelefoneContato(String telefoneContato)` | `void` | Sets the phone number of the contact person.                               |

## Insights
- **Persistence**: The `Supplier` class is designed to be stored in a relational database using JPA. The `@GeneratedValue` annotation ensures that the `id` field is automatically managed by the database.
- **Encapsulation**: The use of private fields with public getter and setter methods ensures controlled access to the data, adhering to object-oriented principles.
- **Brazilian Context**: The inclusion of the `cnpj` field suggests that the class is tailored for use in a Brazilian business context, as CNPJ is specific to Brazil.
- **Contact Information**: The class provides fields for storing detailed contact information, making it suitable for applications that require communication with suppliers.
