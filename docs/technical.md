# **Technical Docs - LearnX LMS**

## **1. Architecture Overview (AWS)**

**LearnX** is a role-based Learning Management System (LMS) connecting **Instructors** and **Students** through a secure, scalable web platform.
It follows a modular **MERN stack architecture** for seamless integration and deployment.

![logo](assets/aws.png)

## **2. Authentication Flow**

Authentication ensures that only valid **Instructors** and **Students** can access LearnX.
Users log in or sign up using email and password.

```mermaid
flowchart TD
    A[Open Login Page] --> B[Enter Email & Password]
    B --> C[Send Credentials to Server]
    C --> D[Verify in Database]
    D -->|Valid| E[Generate JWT Token]
    D -->|Invalid| F[Show Error Message]
    E --> G{User Role}
    G -->|Instructor| H[Redirect to Instructor Dashboard]
    G -->|Student| I[Redirect to Student Dashboard]
```

**Purpose:**

- Secure user login
- Prevent unauthorized access

---

## **3. Authorization Flow**

After login, the system checks the user’s role and grants access accordingly. Instructors can manage courses, while students can browse, enroll, and watch lessons.

```mermaid
flowchart TD
    A[Login Successful] --> B[Check Role]
    B -->|Instructor| C[Instructor Dashboard]
    C --> D[Create / Edit / Delete Courses]
    C --> E[View Enrolled Students]
    B -->|Student| F[Student Dashboard]
    F --> G[Browse & Enroll Courses]
    F --> H[Watch Lessons]
```

---

## **4. Planned Tech Setup**

| <span style="font-size:1.3em; font-weight:700;">**Layer**</span>                       | <span style="font-size:1.3em; font-weight:700;">**Technology**</span>                                                                                                |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span style="font-size:1.15em; font-weight:700;">**Frontend**</span>                   | <img src="https://skillicons.dev/icons?i=js,react,tailwind,vite" alt="JavaScript, React, Tailwind, Vite"/>                                                           |
| <span style="font-size:1.15em; font-weight:700;">**Backend**</span>                    | <img src="https://skillicons.dev/icons?i=nodejs,express" alt="Node.js, Express"/>                                                                                    |
| <span style="font-size:1.15em; font-weight:700;">**Database**</span>                   | <img src="https://skillicons.dev/icons?i=mongodb,mongoose" alt="MongoDB, Mongoose"/>                                                                                 |
| <span style="font-size:1.15em; font-weight:700;">**Media Storage**</span>              | <img src="https://raw.githubusercontent.com/tandpfun/skill-icons/231498caad5aa2ab9f05c4b6410fb5f7a8d3e424/icons/Cloudinary-Dark.svg" width="50px" alt="Cloudinary"/> |
| <span style="font-size:1.15em; font-weight:700;">**Payment Integration (Test)**</span> | <img src="https://cdn-icons-png.flaticon.com/128/174/174861.png" width="50px" alt="PayPal"/>                                                                         |
| <span style="font-size:1.15em; font-weight:700;">**Authentication**</span>             | <img src="https://img.icons8.com/?size=96&id=rHpveptSuwDz&format=png" width="50px" alt="JWT"/>                                                                       |
| <span style="font-size:1.15em; font-weight:700;">**Mobile App**</span>                 | <img src="https://blog.openreplay.com/images/building-a-pwa-with-react/images/hero.png" width="50px" alt="React+PWA"/>                                               |
| <span style="font-size:1.15em; font-weight:700;">**Hosting & Deployment**</span>                | <img src="https://skillicons.dev/icons?i=github,aws,githubactions" alt="AWS"/>        

---

## **5. Data Flow Diagram (DFD)**

The Data Flow Diagram (DFD) represents how data flows within the **LearnX LMS** platform. It visually explains how users (students and instructors) interact with the system and how data is processed, stored, and managed across different components.

---

### **DFD Level 0 - Context Diagram**

This level provides an overview of the complete system. It shows how **students** and **instructors** communicate with the **LearnX LMS**, which handles authentication, course management, and media storage using **MongoDB Atlas** and **Cloudinary**.

![logo](assets/dfd_level0.png)

---

### **DFD Level 1 - System Process Breakdown**

The Level 1 diagram expands the system into key functional processes **Authentication**, **Course Management**, and **Course Completion**. It illustrates how data moves between users, the database, and external services to support secure login, course handling, and student progress.

![logo](assets/dfd_level1.png)

---

## **6. Conclusion**

**LearnX LMS** uses secure authentication and role-based authorization to provide:

- Clear separation of **Instructor** and **Student** views
- Safe and scalable system
- Ready for future features like progress tracking and payments
