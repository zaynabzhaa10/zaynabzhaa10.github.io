---
layout: post
title: "Introduction to Selenium WebDriver: Automating Web Testing with Precision"
date: 2025-10-07 09:00:00 +0800
categories: [Articles, SoftwareTesting]
tags: [Software Testing, Selenium, WebDriver, Automation, Python, QA, STQA]
image:
    path: "/assets/selenium_webdriver.png"
---

## Introduction

In today’s web-driven era, **automated testing** has become a crucial part of software quality assurance.  
One of the most widely used tools in this domain is **Selenium WebDriver** — an open-source framework for browser automation.

This article summarizes the presentation from **Kelompok 7 Sistem Informasi 2023**, exploring what Selenium is, why it’s widely used, how it interacts with browsers, and how to implement a simple test scenario using Python.

---

## What Is Selenium?

**Selenium** is an open-source framework for automating web browsers.  
It enables testers and developers to simulate real user interactions such as clicking, typing, navigating, and validating web elements.

Selenium supports multiple **programming languages** including:
- Python  
- Java  
- C#  
- JavaScript  

And works across various **browsers**:
- Google Chrome  
- Mozilla Firefox  
- Microsoft Edge  
- Safari  

---

## What Is Selenium WebDriver?

**WebDriver** is the **core component** of Selenium.  
It acts as the bridge between the automation code and the browser.

### WebDriver Functions:
- Opens and closes browsers automatically  
- Simulates user actions (clicks, text input, scrolling, etc.)  
- Validates page elements and results  
- Navigates through URLs and form submissions  

Essentially, it gives your code “hands” to interact with a live web browser.

---

## Why Use Selenium?

There are many reasons why **Selenium** is one of the most popular choices for web automation testing.

| Reason | Explanation |
|---------|--------------|
| **Free and Open Source** | Completely free with an active community. |
| **Multi-Language Support** | Works with Python, Java, JavaScript, C#, etc. |
| **Cross-Platform Compatibility** | Runs on Windows, macOS, and Linux. |
| **Multi-Browser Support** | Works seamlessly with Chrome, Firefox, Edge, Safari. |
| **Integration Ready** | Integrates easily with frameworks like **PyTest**, **JUnit**, or **TestNG**. |
| **Rich Ecosystem** | Strong documentation and community support. |

---

## Installing Selenium with Python

You can install Selenium in just one command using `pip`:

```bash
pip install selenium
```
Then, download the WebDriver for your browser (e.g., ChromeDriver for Chrome).
ChromeDriver: https://chromedriver.chromium.org/downloads
GeckoDriver (Firefox): https://github.com/mozilla/geckodriver/releases
Place the driver file in your project folder or add it to your system PATH.

## Opening a Browser with Selenium
Here’s a simple Python example to open a browser using Selenium:
```python
from selenium import webdriver

# Initialize WebDriver
driver = webdriver.Chrome()

# Open a website
driver.get("https://www.saucedemo.com/")

# Close browser after 5 seconds
import time
time.sleep(5)
driver.quit()
```
This script will automatically launch Chrome, open the specified URL, and then close it after a few seconds.

## Interacting with HTML Elements
You can use Selenium to find and interact with HTML elements such as buttons, input fields, and links.
```python
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get("https://www.saucedemo.com/")

# Input username and password
driver.find_element(By.ID, "user-name").send_keys("standard_user")
driver.find_element(By.ID, "password").send_keys("secret_sauce")

# Click login button
driver.find_element(By.ID, "login-button").click()

# Close after viewing
import time
time.sleep(5)
driver.quit()
```
Explanation:
- find_element(By.ID, "user-name") → Finds an element by its HTML ID.
- send_keys() → Types text into an input field.
- click() → Simulates a button click.

## Test Scenarios with Selenium
Below are some test scenarios demonstrated by the group during their session, using the SauceDemo website as an example.
| ID         | Description         | Steps                                                  | Expected Result                    |
| ---------- | ------------------- | ------------------------------------------------------ | ---------------------------------- |
| **TS-001** | Successful login    | Input `standard_user` and `secret_sauce` → Click Login | User enters the **inventory page** |
| **TS-002** | Failed login        | Input invalid credentials → Click Login                | Displays **error message**         |
| **TS-003** | Add product to cart | Login → Click **Add to Cart**                          | Cart count increases by 1          |

## Example Test Case (Login Success)
```python
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get("https://www.saucedemo.com/")

# Step 1: Enter credentials
driver.find_element(By.ID, "user-name").send_keys("standard_user")
driver.find_element(By.ID, "password").send_keys("secret_sauce")

# Step 2: Click Login
driver.find_element(By.ID, "login-button").click()

# Step 3: Verify redirection
assert "inventory" in driver.current_url

print("✅ Login Test Passed")
driver.quit()
```
If the login is successful, the script will confirm that the user is redirected to the inventory page.

## Example: Adding a Product to Cart
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

driver = webdriver.Chrome()
driver.get("https://www.saucedemo.com/")

# Login
driver.find_element(By.ID, "user-name").send_keys("standard_user")
driver.find_element(By.ID, "password").send_keys("secret_sauce")
driver.find_element(By.ID, "login-button").click()

# Add to cart
driver.find_element(By.XPATH, "//button[text()='Add to cart']").click()

# Verify cart
cart_count = driver.find_element(By.CLASS_NAME, "shopping_cart_badge").text
assert cart_count == "1"

print("✅ Product successfully added to cart")

time.sleep(3)
driver.quit()
```

## Advantages of Selenium WebDriver
| Advantage                  | Description                                               |
| -------------------------- | --------------------------------------------------------- |
| **Automation Efficiency**  | Reduces repetitive manual testing.                        |
| **Cross-Browser Testing**  | Ensures consistent results across browsers.               |
| **Cost-Effective**         | Open-source with no licensing costs.                      |
| **Integration-Friendly**   | Works with CI/CD tools like Jenkins, GitHub Actions, etc. |
| **Improves Test Accuracy** | Eliminates human error in repetitive tasks.               |

## Conclusion

Selenium WebDriver is a powerful and flexible tool for automating browser actions.
It helps QA engineers validate web applications more efficiently while saving time and ensuring consistency.

By integrating Selenium with frameworks like PyTest or JUnit, developers can build reliable automation suites that form the foundation of modern software testing.

### 👥 Contributors

Kelompok 7 Sistem Informasi 2023:

1. Fitriani Jaya (H071231012)
2. Muhammad Qaffal Al Fifaiz (H071231032)
3. Muslih Khairu Alief Rahman (H071231042)
4. Diza Sazkia (H071231043)
5. Arelio Junara Palinoan (H071231047)
6. Ivan Betrandi (H071231038)
7. Sheryl Anastasya Palambang (H071231059)
8. Novi Rezkiyah Azzahrah Ramadhani (H071231069)
9. Wahyu Rusman (H071231068)

**Summarized by: Zainab Muchsinin**