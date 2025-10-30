---
layout: post
title: "Test Scenario, Test Case, and Bug Report: Core Components of Software Testing"
date: 2025-10-04 09:00:00 +0800
categories: [Articles, SoftwareTesting]
tags: [Software Testing, Test Case, Test Scenario, Bug Report, QA, SDLC]
image:
    path: "/assets/test_scenario.png"
---

## Introduction

In the software testing process, three interconnected elements are essential to ensure the quality and reliability of an application:  
**Test Scenario**, **Test Case**, and **Bug Report**.  

These three components work together to help QA teams validate software behavior, identify issues early, and maintain consistent functionality throughout development.

This article summarizes the material from **Kelompok 4 Sistem Informasi 2023**, focusing on how these components contribute to an effective software testing strategy — using a **BMI Calculator App** as a case study.

---

## Overview of Key Concepts

| Concept | Description |
|----------|--------------|
| **Test Scenario** | Describes *what to test* — a general overview of features or modules to verify. |
| **Test Case** | Describes *how to test* — detailed steps, inputs, and expected results. |
| **Bug Report** | Documents errors found during testing, including how to reproduce and expected outcomes. |

---

## Test Scenario

A **Test Scenario** defines the *scope* of testing by describing which functionality or feature will be verified.  
It helps ensure that all critical features are covered and that no essential module is missed.

### Simple Test Scenario Template

| Field | Description |
|--------|-------------|
| **ID Scenario** | Unique identifier for the scenario |
| **Description** | Brief summary of what will be tested |
| **Module/Feature** | Specific system area or function being tested |

### Example – BMI Calculator App

| ID | Description | Module/Feature |
|----|--------------|----------------|
| TS001 | Check slider input function | Slider for height and weight |
| TS002 | Verify BMI calculation and classification | BMI calculation module |
| TS003 | Check BMI history saving function | History management module |

---

## Test Case

A **Test Case** provides a step-by-step guide to executing a specific scenario.  
It includes *preconditions, inputs, expected results,* and *actual results*.

### Simple Test Case Template

| Field | Description |
|--------|-------------|
| **ID Test Case** | Unique ID for each test |
| **Description** | Summary of what the test verifies |
| **Precondition** | Conditions that must be met before testing |
| **Test Steps** | Step-by-step actions performed during testing |
| **Test Data** | Data used for input |
| **Expected Result** | The predicted outcome if the feature works correctly |
| **Actual Result** | The real outcome after testing |
| **Status** | Pass / Fail |

---

### Example Test Cases for BMI Calculator

#### Scenario ID: TS001 — Slider Input Function

| ID | Description | Precondition | Test Steps | Test Data | Expected Result |
|----|--------------|---------------|-------------|-------------|----------------|
| TC001 | Verify weight slider input | App open | 1. Move weight slider to 60kg <br> 2. Check value displayed | 60 kg | Label shows “60 kg” |
| TC002 | Verify height slider input | App open | 1. Move height slider to 170cm <br> 2. Check value displayed | 170 cm | Label shows “170 cm” |

#### Scenario ID: TS002 — BMI Calculation & Classification

| ID | Description | Test Data | Expected Result |
|----|--------------|------------|----------------|
| TC003 | Verify BMI calculation using standard formula (kg/m²) | Height = 170 cm, Weight = 65 kg | BMI = 22.49 (Normal range) |
| TC004 | Verify “Underweight” category | Height = 170 cm, Weight = 45 kg | BMI = 15.6 → Category: Underweight |
| TC005 | Verify “Normal” category | Height = 165 cm, Weight = 60 kg | BMI = 22.04 → Category: Normal |
| TC006 | Verify “Overweight” category | Height = 170 cm, Weight = 75 kg | BMI = 25.95 → Category: Overweight |
| TC007 | Verify “Obese” category | Height = 165 cm, Weight = 90 kg | BMI = 33.06 → Category: Obese |

#### Scenario ID: TS003 — History Functionality

| ID | Description | Precondition | Test Steps | Expected Result |
|----|--------------|---------------|-------------|----------------|
| TC008 | Verify saving of latest BMI result to history | App open | 1. Input BMI data <br> 2. Click “Save History” | Data stored in history page |
| TC009 | Verify multiple history entries | Previous data saved | Save multiple BMI results | All entries displayed correctly without data loss |

---

## Bug Report

A **Bug Report** is a formal record of software defects discovered during testing.  
It documents issue details, impact level, and steps to reproduce errors.

### Standard Bug Report Template

| Field | Description |
|--------|-------------|
| **Bug ID** | Unique identifier for each issue |
| **Bug Title** | Short description of the issue |
| **Steps to Reproduce** | Detailed steps to trigger the bug |
| **Expected Result** | What should happen |
| **Actual Result** | What actually happened |
| **Severity** | How severe the bug is (Low → Critical) |
| **Priority** | Urgency level for fixing (P1–P4) |
| **Assignee** | Person responsible for fixing |
| **Reporter** | QA tester who found the bug |
| **Environment** | Platform or device tested |
| **Reported On** | Date of discovery |

---

### Example Bug Report — BMI Calculation Error

| Field | Value |
|--------|--------|
| **Bug ID** | BMI-001 |
| **Bug Title** | Incorrect BMI result when input weight = 60kg, height = 170cm |
| **Steps to Reproduce** | 1. Open BMI app <br> 2. Input weight = 60, height = 170 <br> 3. Click “Calculate” |
| **Expected Result** | BMI = 20.8 |
| **Actual Result** | BMI = 12.5 |
| **Severity** | Major (High) |
| **Priority** | P2 – High |
| **Build Number** | Version 1.0.0 |
| **Environment** | Android |
| **Assignee** | Developer |
| **Reporter** | QA Engineer |
| **Reported On** | 31-08-2025 |

---

## Severity and Priority Levels

| Severity | Description |
|-----------|--------------|
| **Low** | Does not impact core functions; minor issue. |
| **Minor (Medium)** | Small visual or usability issue that causes inconvenience. |
| **Major (High)** | Core functionality fails but system still runs. |
| **Critical** | Causes total system failure or data corruption. |

| Priority | Description |
|-----------|--------------|
| **P1 (Critical)** | Must be fixed immediately before release. |
| **P2 (High)** | Important issue affecting multiple users. |
| **P3 (Medium)** | Can be fixed in the next release. |
| **P4 (Low)** | Cosmetic or minor issue; fix anytime. |

---

## How to Prevent Bugs

To reduce defects and improve software quality, teams should apply good development and testing practices throughout the SDLC.

### Best Practices:
1. **Understand Requirements Clearly**  
   Ensure all team members have a shared understanding of project specifications.  
2. **Perform Unit Testing**  
   Detect issues early during development.  
3. **Code Review**  
   Encourage peer reviews to catch logical or syntax errors.  
4. **Create a Comprehensive Test Plan**  
   Define objectives, methods, and schedules before testing.  
5. **Use Automated Testing Tools**  
   Accelerate testing and ensure consistency.  
6. **Promote Team Collaboration**  
   Strengthen communication between developers and testers to prevent misinterpretation.

---

## Conclusion

**Test Scenario**, **Test Case**, and **Bug Report** are essential documentation pillars in software testing.  
They ensure that the product works as intended, every defect is traceable, and the final release meets user expectations.

Combining structured testing and good collaboration practices leads to **higher software quality, fewer bugs, and happier users.**

---

### 👥 Contributors

**Kelompok 4 Sistem Informasi 2023:**
- Sisy Ramadhani (H071231006)  
- Ilham Kurniawan (H071231024)  
- Muh. Naufal Fahri Salim (H071231031)  
- A. Tasdik Bijaksana (H071231041)  
- Fathan Wibowo (H071231053)  
- Kezia Dewanti Putri Ayu Tappi (H071231070)  
- Imam Ahmad Mirza (H071231082)  
- Khalika Tsabitah Malik (H071231084)

---

**Summarized by: Zainab Muchsinin**
