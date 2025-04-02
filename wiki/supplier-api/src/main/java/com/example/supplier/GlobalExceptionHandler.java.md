# Documentation: `GlobalExceptionHandler.java`

## Overview
The `GlobalExceptionHandler` class is a centralized exception handling mechanism for a Spring Boot application. It uses the `@ControllerAdvice` annotation to intercept and handle exceptions thrown by controllers globally. This approach ensures consistent error responses across the application.

## Features
- **Centralized Exception Handling**: Handles exceptions globally for all controllers in the application.
- **Custom Error Responses**: Returns structured error responses with HTTP status codes and descriptive messages.
- **Support for Multiple Exception Types**: Handles specific exceptions (`ConstraintViolationException`, `IllegalArgumentException`) and generic exceptions (`Exception`).

## Class Details

### Annotations
- `@ControllerAdvice`: Indicates that this class provides global exception handling for controllers.
- `@ExceptionHandler`: Specifies the type of exception to handle and maps it to a handler method.

### Methods

| Method Name                              | Exception Type                  | HTTP Status Code         | Description                                                                 |
|------------------------------------------|----------------------------------|--------------------------|-----------------------------------------------------------------------------|
| `handleConstraintViolationException`     | `ConstraintViolationException`  | `HttpStatus.BAD_REQUEST` | Handles validation errors caused by constraint violations.                 |
| `handleIllegalArgumentException`         | `IllegalArgumentException`      | `HttpStatus.BAD_REQUEST` | Handles errors caused by invalid arguments passed to methods.              |
| `handleException`                        | `Exception`                     | `HttpStatus.INTERNAL_SERVER_ERROR` | Handles generic exceptions and logs the stack trace for debugging purposes. |

### Error Response Structure
The error response returned by the handler methods is encapsulated in the `ErrorResponse` class. It typically includes:
- **Status Code**: The HTTP status code as a string.
- **Message**: A descriptive error message.

## Insights
- **Scalability**: The use of `@ControllerAdvice` makes the application scalable by allowing new exception handlers to be added easily.
- **Error Logging**: The `handleException` method logs the stack trace, aiding in debugging unexpected errors.
- **Validation Handling**: The `ConstraintViolationException` handler ensures that validation errors are communicated clearly to the client.
- **Consistency**: All error responses follow a consistent structure, improving client-side error handling.

## Dependencies
- **Spring Framework**: Provides annotations like `@ControllerAdvice` and `@ExceptionHandler`.
- **Jakarta Validation**: Used for handling validation-related exceptions (`ConstraintViolationException`).

## File Metadata
- **File Name**: `GlobalExceptionHandler.java`
