# DevOps Class Notes – Day 1

## Topics

- [SDLC](#1-sdlc-software-development-life-cycle)
- [Waterfall vs Agile vs DevOps](#4-waterfall-vs-agile-vs-devops)
- [Different Environments](#5-different-environments)
- [What is DevOps](#definition-of-devops)

---

# 1. SDLC (Software Development Life Cycle)

SDLC is the complete process followed to build software applications in a structured manner.

## Stages of SDLC

1. **Requirements Gathering**

   * Collect business requirements
   * Understand customer needs

2. **Planning**

   * Budget estimation
   * Timeline planning
   * Resource allocation

3. **Analysis**

   * Analyze feasibility
   * Understand technical challenges

4. **Design**

   * Design architecture and workflow
   * Database and UI planning

5. **Development / Construction**

   * Developers write application code

6. **Testing**

   * Validate application functionality
   * Find defects/bugs

7. **Deployment / Handover**

   * Release application to users

8. **Maintenance & Monitoring**

   * Fix issues
   * Improve performance
   * Continuous monitoring

---

# 2. Goal of Software Systems

Business + Technology work together to:

* Reduce cost
* Increase stability
* Improve reliability
* Increase business growth
* Improve customer satisfaction

---

# 3. Stakeholders

Stakeholders are people involved directly or indirectly in the system/project.

## Example: School System

Stakeholders:

* Parents
* Students
* Teachers
* Management
* Non-teaching staff
* Investors
* Government

## Example: Banking Project

Stakeholders:

* RBI
* Government
* Banking management
* Investors
* Board of Directors
* Developers
* Testing team
* Admin team
* DevOps & Cloud team
* Support team
* Monitoring & Reporting teams

---

# 4. Waterfall vs Agile vs DevOps

---

# Waterfall Model

Traditional software development approach.

## Process

* Requirements collected once
* Development happens completely
* Testing happens at the end
* Deployment after everything finishes

## Example

### Final Exam System (Old Education Model)

* Teachers complete syllabus
* Students study near final exams
* Parents worry throughout the year
* Only one major feedback cycle

### Result

* 30–40% pass percentage

---

## Software Example

* Project duration: 3 years
* Budget: 30 Crores
* Development for 6–7 months continuously
* Testing only after development completes

### Problems

* Testing finds 100 defects
* Developers may already move to other work
* 40 defects may become invalid defects
* “Working in DEV but not working in PROD” issues
* Slow feedback cycle

---

# Agile Model

Agile divides the project into smaller modules and shorter cycles called **Sprints**.

## Example Modules

* User Management
* Cart
* Catalogue
* Shipping
* Payment
* Order Management
* Reviews
* Delivery

---

## Sprint Model

### Sprint Duration

Usually 2 weeks to 1 month.

### Example Sprint

User Module:

* Login
* Signup
* Forgot Password
* OTP

---

## Agile Workflow

* Development starts from Day-1
* Testing starts early
* Continuous feedback
* End of sprint → working demo shown to client

---

## Daily Agile Meetings

### Daily Standup Meeting (DSM)

Questions:

1. What did you do yesterday?
2. What are you doing today?
3. Is anything blocking you?

---

## Advantages of Agile

* Faster feedback
* Better coordination
* Improved productivity
* Lower invalid defects
* Early issue detection

---

## Education Analogy for Agile

### Unit Tests Instead of Final Exam

* Unit Test-I
* Unit Test-II
* Quarterly
* Half-yearly
* Pre-final
* Final

### Result

* Continuous improvement
* Parents and teachers receive feedback regularly
* Pass percentage improves to 80–90%

---

# DevOps Model

DevOps extends Agile by introducing:

* Continuous Development
* Continuous Integration
* Continuous Testing
* Continuous Deployment
* Continuous Monitoring
* Continuous Feedback

---

# Definition of DevOps

DevOps is the process of building, testing, deploying, and monitoring applications continuously using automation and collaboration.

Goal:

> Deploy and test code on the same day to maximize feedback cycles and improve the product faster.

---

# Real-Time Example of DevOps

## Apple Watch Example

Apple Watch continuously collects:

* Health data
* User activity
* Feedback

This creates continuous monitoring and continuous improvement.

---

# Daily Slip Test Analogy

* 200 small tests = 200 feedback cycles
* Immediate corrections possible

### Result

* 99.9% success rate

---

# Important Concept

> If you test a system 1 time → you may find 10 defects
> If you test a system 100 times → you may find at least 11 defects

Meaning:

* Continuous testing improves software quality significantly.

---

# 5. Different Environments

Software passes through multiple environments before production.

---

## DEV Environment

### Purpose

Developers test their own code.

### Example

“Test the drink yourself.”

---

## QA Environment

### Purpose

Testing team validates application.

### Example

Employees taste the drink and provide feedback.

---

## SIT (System Integration Testing)

### Purpose

Check integration between multiple modules.

### Example

Friends and family test the drink.

---

## UAT (User Acceptance Testing)

### Purpose

Real users validate business requirements.

### Example

Random customers test the drink.

---

## PERF Environment

### Purpose

Performance and load testing.

Checks:

* Speed
* Scalability
* Stability under heavy traffic

---

## PRE-PROD Environment

### Purpose

Production-like environment before final release.

Final verification happens here.

---

## PROD Environment

### Purpose

Live application used by real customers.

Example:
Application released to public market.

---

# 6. Testing Concepts

---

## Positive Test Cases (+ve)

Valid inputs should produce successful results.

Example:

* Correct username/password
* Login success

---

## Negative Test Cases (-ve)

Invalid inputs should fail properly.

Example:

* Wrong password
* Invalid OTP

---

# 7. Types of Errors

1. Build Errors
2. Functionality / Development Errors
3. Deployment Errors

---

# 8. DevOps Benefits

* Faster deployments
* Faster feedback cycles
* Better collaboration
* Reduced cost
* Improved software quality
* Increased automation
* Continuous monitoring
* Better business growth

---

# 9. Digital Transformation

Companies invest in:

* Cloud
* Automation
* DevOps
* Monitoring tools

Goal:

* Reduce operational costs
* Improve market share
* Improve customer experience

Example:
A bank investing in technology can reduce costs and increase business growth.

---

# 10. Additional Notes

## AWS Free Tier Update

* Around 15th July changes introduced
* New accounts may receive:

  * $100 credits + additional credits

---

## AWS Account Creation Tips

* Enable:

  * International transactions
  * Online spending
  * Net banking if required

* Some cards/banks may block international payments:

  * Example: SBI/RuPay sometimes requires customer care approval

* Use:

  * Correct bank address
  * Name matching PAN card/bank card

---

# Summary

| Model     | Feedback Speed | Testing        | Deployment |
| --------- | -------------- | -------------- | ---------- |
| Waterfall | Very Slow      | End of project | One-time   |
| Agile     | Faster         | Every sprint   | Frequent   |
| DevOps    | Continuous     | Continuous     | Continuous |

---

# Key Takeaway

> More feedback cycles = Better quality software

Waterfall → Late feedback
Agile → Frequent feedback
DevOps → Continuous feedback + automation
