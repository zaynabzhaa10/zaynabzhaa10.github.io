---
layout: post
title: "Introduction to Unit Testing: Building Reliable Code from the Ground Up"
date: 2025-10-05 09:00:00 +0800
categories: [Articles, SoftwareTesting]
tags: [Software Testing, Unit Testing, Pytest, JUnit, Jest, QA, Software Quality]
image:
    path: "/assets/unit_testing.png"
---

## Introduction

Have you ever wanted to **code without fear of bugs**?  
That’s where **Unit Testing** becomes the key.  

Unit testing is one of the earliest and most essential phases of **software testing**, focusing on testing individual components such as **functions, methods, or classes**. It ensures each “unit” of the software works correctly before integrating them into the full system.

This article summarizes the presentation by **Kelompok 5 Sistem Informasi 2023**, which explains the **importance, methodology, and frameworks** of Unit Testing — along with real code examples using **PyTest** and **JUnit**.

---

## What Is Unit Testing?

**Unit Testing** is a software testing method that isolates and tests the smallest components of a program individually.  
It focuses on validating whether each function or module performs as expected without depending on other parts of the system.

**Analogy:**  
It’s like checking each car component (engine, brakes, lights) separately before assembling the full car.  
If every part works perfectly, the complete product will be reliable.

---

## Why Unit Testing Is Important

Unit testing provides both developers and QA teams with confidence that the code is **reliable**, **maintainable**, and **free from critical bugs**.  

Here’s why it matters:

| Benefit | Description |
|----------|--------------|
| **Early Bug Detection** | Identify logic or syntax errors before integration. |
| **Improves Code Quality** | Ensures each function behaves as expected. |
| **Saves Time and Cost** | Fixing bugs early reduces overall project expense. |
| **Simplifies Refactoring** | Easier to modify code without breaking functionality. |
| **Living Documentation** | Unit tests describe system behavior directly in code. |
| **Boosts Developer Confidence** | Makes deployments safer and faster. |

---

## The AAA Pattern: Arrange, Act, Assert

The **AAA pattern** is a popular structure used when writing unit tests. It divides test logic into three clear stages:

| Step | Description |
|------|--------------|
| **Arrange** | Set up the initial state, variables, and dependencies required for testing. |
| **Act** | Execute the function or method being tested. |
| **Assert** | Verify whether the output matches the expected result. |

Example (in Python with PyTest):

```python
def add(a, b):
    return a + b

def test_addition():
    # Arrange
    num1, num2 = 2, 3

    # Act
    result = add(num1, num2)

    # Assert
    assert result == 5
```
### Popular Unit Testing Frameworks

Each programming language has its own unit testing ecosystem.
Here are the three most commonly used frameworks across platforms:
| Framework   | Language   | Key Features                                                         | When to Use                                                           |
| ----------- | ---------- | -------------------------------------------------------------------- | --------------------------------------------------------------------- |
| **JUnit 5** | Java       | Annotation-based structure, strong IDE integration, mature ecosystem | When building apps with Java, Kotlin, or other JVM-based languages    |
| **PyTest**  | Python     | Simple syntax, detailed reports, strong fixture system               | For Python projects — from small scripts to data science and web apps |
| **Jest**    | JavaScript | Zero configuration, snapshot testing, async support                  | For frontend or Node.js apps (React, TypeScript, etc.)                |

### Example 1: Using PyTest (Python)
Test Case: Shopping Cart Calculation
```python
# shopping_cart.py
def calculate_total(prices):
    return sum(prices)

# test_shopping_cart.py
from shopping_cart import calculate_total

def test_calculate_total():
    prices = [10, 20, 30]
    result = calculate_total(prices)
    assert result == 60
```
Output:
All tests passed successfully.

### Example 2: Using JUnit 5 (Java)
Test Case: Bank Account Balance Validation

```python
// BankAccount.java
public class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }

    public void deposit(double amount) {
        balance += amount;
    }

    public double getBalance() {
        return balance;
    }
}

// BankAccountTest.java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class BankAccountTest {
    @Test
    void testDeposit() {
        BankAccount account = new BankAccount(100);
        account.deposit(50);
        assertEquals(150, account.getBalance());
    }
}
```
Result:
The test passes, confirming that the deposit function updates the balance correctly.

## Verification and Test Results
After executing unit tests:
Passed tests confirm that functionality works correctly.
Failed tests indicate a logical or implementation error that must be fixed.
Tools like PyTest, JUnit, and Jest provide detailed test reports showing which cases passed, failed, or were skipped — making debugging faster and more efficient.

## Live Coding Summary
In the presentation, Kelompok 5 demonstrated two hands-on unit testing sessions:
🧮 Shopping Cart — using PyTest (Python)
🏦 Bank Account — using JUnit 5 (Java)
Both examples highlight how unit tests can validate individual functions efficiently before integration with larger systems.

## Conclusion

Unit Testing is the foundation of reliable and maintainable software.
By testing small units of code early, developers prevent critical bugs, reduce costs, and improve product stability.

Whether using PyTest, JUnit, or Jest, unit testing empowers teams to write code that is both robust and fearless.

### 👥 Contributors

Kelompok 5 Sistem Informasi 2023:
Zaenab Putri Az Zakiyyah (H071231001)
Nancy Jiwono (H071231004)
Rudy Peter (H071231015)
Cholyn Sharon Enos (H071231040)
Andi Aisar Saputra Dwi Anna (H071231048)
M. Ervin (H071231050)
Fara Rahmasari Fahirun (H071231055)
Harmelia Yuli Rahmatika A. (H071231079)

**Summarized by: Zainab Muchsinin**