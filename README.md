# 📦 Inventory Management System (TypeScript)

A backend-focused **Inventory Management System** built with **TypeScript**, designed to demonstrate clean architecture, explicit error handling, and real-world backend design principles.

This project prioritizes **correctness, structure, and scalability** over UI complexity.

---

## 🎯 Project Goals

The goal of this project is to build a system that can:

- Manage products and inventory levels
- Enforce business rules at the domain level
- Prevent invalid operations (e.g. negative stock)
- Be easy to test, extend, and reason about
- Reflect real-world backend architecture used in production systems

This project is intentionally **backend-first**.

---

## 🧠 Key Concepts Demonstrated

- Layered Architecture
- Domain-driven design (DDD-inspired)
- Explicit error handling using `Result` types
- Separation of concerns
- Testable business logic
- TypeScript strict mode best practices

---

## 🏗️ Architecture Overview

The project follows a **Layered Architecture**:


Each layer has a single responsibility and depends only on layers **below** it.

### Why this matters
- Business rules are protected
- Infrastructure can change without breaking logic
- Code is easier to test and maintain

---

## 📁 Project Structure

```
src/
├── domain/ # Core business rules
│ ├── entities/ # Domain entities (e.g. Product)
│ ├── value-objects/ # Strongly-typed domain values
│ ├── errors/ # Domain-specific errors
│ └── repositories/ # Repository interfaces
│
├── application/ # Use cases / business workflows
│ ├── use-cases/
│ └── dtos/
│
├── infrastructure/ # Technical implementations
│ ├── persistence/
│ │ └── in-memory/
│ └── config/
│
├── interfaces/ # External interfaces (HTTP, etc.)
│ └── http/
│ ├── controllers/
│ ├── routes/
│ └── middlewares/
│
├── shared/ # Cross-cutting concerns
│ ├── result/ # Result / Either types
│ └── errors/
│
└── main.ts # Application entry point
tests/
├── domain/
├── application/
└── infrastructure/
```

---

## 🔁 Error Handling Philosophy

This project **does not rely on exceptions** for business logic.

Instead, it uses explicit return types:

## Result<SuccessType, ErrorType>


### Benefits
- Predictable control flow
- No hidden runtime surprises
- Easier testing
- Clear intent at call sites

---

## 🧪 Testing Strategy

Testing focuses on **behavior**, not implementation details.

### What is tested
- Domain rules (e.g. stock cannot go below zero)
- Use cases (e.g. duplicate SKU prevention)
- Error scenarios

### Tools
- **Vitest**

Tests are organized by layer to reflect responsibility boundaries.
