# **Technical Docs - LearnX LMS**

## **1. Authentication (Planned Flow)**

Authentication will ensure that only valid users (Instructor or Student) can access LearnX.
Users will sign up or log in with basic credentials (like email and password).

```mermaid
flowchart TD
    A[User Opens Login Page] --> B[Enter Email & Password]
    B --> C[Send Credentials to Server]
    C --> D[Verify User in Database]
    D -->|Valid| E[Generate Token & Based on User/Instructor]
    D -->|Invalid| F[Show Error Message]
    E --> G[Redirect to Dashboard]
```

**Purpose:**

* Secure user login
* Prevent unauthorized access

---

## **2. Authorization (Planned Flow)**

Once authenticated, users will access pages based on their roles.

```mermaid
flowchart TD
    A[User Logs In] --> B[System Checks Role]
    B -->|Instructor| C[Access Instructor Dashboard]
    B -->|Student| D[Access Student Dashboard]
    B -->|Unauthorized| E[Access Denied / Redirect to Login]
```

**Goal:**

* Ensure that **Instructors** can create/manage courses
* Ensure that **Students** can view/enroll in courses
* Keep all admin-level operations secure

---

## **3. Planned Tech Setup**

| <span style="font-size:1.3em; font-weight:700;">**Layer**</span> | <span style="font-size:1.3em; font-weight:700;">**Technology**</span> |
|-------------------------------------------------------------------|----------------|
| <span style="font-size:1.15em; font-weight:700;">**Frontend**</span> | <img src="https://skillicons.dev/icons?i=js,react,tailwind,vite" alt="JavaScript, React, Tailwind, Vite"/> |
| <span style="font-size:1.15em; font-weight:700;">**Backend**</span> | <img src="https://skillicons.dev/icons?i=nodejs,express" alt="Node.js, Express"/> |
| <span style="font-size:1.15em; font-weight:700;">**Database**</span> | <img src="https://skillicons.dev/icons?i=mongodb,mongoose" alt="MongoDB, Mongoose"/> |
| <span style="font-size:1.15em; font-weight:700;">**Media Storage**</span> | <img src="https://raw.githubusercontent.com/tandpfun/skill-icons/231498caad5aa2ab9f05c4b6410fb5f7a8d3e424/icons/Cloudinary-Dark.svg" width="50px" alt="Cloudinary"/> |
| <span style="font-size:1.15em; font-weight:700;">**Payment Integration (Test)**</span> | <img src="https://cdn-icons-png.flaticon.com/128/174/174861.png" width="50px" alt="PayPal"/> |
| <span style="font-size:1.15em; font-weight:700;">**Authentication**</span> | <img src="https://img.icons8.com/?size=96&id=rHpveptSuwDz&format=png" width="50px" alt="JWT"/> |
| <span style="font-size:1.15em; font-weight:700;">**Mobile App**</span> | <img src="https://blog.openreplay.com/images/building-a-pwa-with-react/images/hero.png" width="50px" alt="React"/>|

---

## **Summary**

This technical plan outlines how authentication and authorization will be implemented in **LearnX LMS** once development starts.
It focuses on:

* A **secure login system**
* **Role-based access**
* **Scalable structure** ready for real-world use
