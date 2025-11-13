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

## **4. Tech Stack**

| **Layer**                      | **Logo**                                                                                                                                                           | **Technology** | **Version** |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------- | ----------- |
| **Programming Language**       | <img src="https://skillicons.dev/icons?i=js" width="32" alt="JavaScript"/>                                                                                         | JavaScript     | ES14        |
| **Frontend Library**           | <img src="https://skillicons.dev/icons?i=react" width="32" alt="React"/>                                                                                           | React          | 19.2.0      |
| **CSS Framework**              | <img src="https://skillicons.dev/icons?i=tailwind" width="32" alt="Tailwind CSS"/>                                                                                 | Tailwind CSS   | 4.1.17      |
| **Build Tool**                 | <img src="https://skillicons.dev/icons?i=vite" width="32" alt="Vite"/>                                                                                             | Vite           | 7.2.2       |
| **Runtime Environment**        | <img src="https://skillicons.dev/icons?i=nodejs" width="32" alt="Node.js"/>                                                                                        | Node.js        | 22.12.0     |
| **Backend Framework**          | <img src="https://skillicons.dev/icons?i=express" width="32" alt="Express"/>                                                                                       | Express        | 5.1.0       |
| **Database**                   | <img src="https://skillicons.dev/icons?i=mongodb" width="32" alt="MongoDB"/>                                                                                       | MongoDB        | 8.0         |
| **Media Storage**              | <img src="https://raw.githubusercontent.com/tandpfun/skill-icons/231498caad5aa2ab9f05c4b6410fb5f7a8d3e424/icons/Cloudinary-Dark.svg" width="32" alt="Cloudinary"/> | Cloudinary     | 1.45.0      |
| **Payment Integration (Test)** | <img src="https://cdn-icons-png.flaticon.com/128/174/174861.png" width="32" alt="PayPal"/>                                                                         | PayPal SDK     | 1.8.0       |
| **Authentication**             | <img src="https://img.icons8.com/?size=96&id=rHpveptSuwDz&format=png" width="32" alt="JWT"/>                                                                       | JWT            | 9.0.2       |
| **Mobile Experience**          | <img src="https://blog.openreplay.com/images/building-a-pwa-with-react/images/hero.png" width="32" alt="React+PWA"/>                                               | React PWA      | Manifest V3 |
| **Cloud Hosting**              | <img src="https://skillicons.dev/icons?i=aws" width="32" alt="AWS"/>                                                                                               | AWS            | Latest      |
| **Version Control**            | <img src="https://skillicons.dev/icons?i=github,githubactions" width="64" alt="GitHub"/>                                                                           | GitHub         | Latest      |

---

## **5. API Endpoints Reference**

### **I. Authentication Endpoints**

| **Endpoint**         | **Method** | **Description**               |
| -------------------- | ---------- | ----------------------------- |
| `/api/auth/register` | POST       | Create new user account       |
| `/api/auth/login`    | POST       | User login and JWT generation |
| `/api/auth/me`       | GET        | Get current user profile      |

### **II. User Endpoints**

| **Endpoint**         | **Method** | **Description**       |
| -------------------- | ---------- | --------------------- |
| `/api/users/profile` | GET        | Get user profile data |
| `/api/users/profile` | PUT        | Update user profile   |

### **III. Course Endpoints**

| **Endpoint**       | **Method** | **Description**                     |
| ------------------ | ---------- | ----------------------------------- |
| `/api/courses`     | GET        | Get all courses (public)            |
| `/api/courses`     | POST       | Create new course (instructor only) |
| `/api/courses/:id` | GET        | Get course details                  |
| `/api/courses/:id` | PUT        | Update course (instructor only)     |
| `/api/courses/:id` | DELETE     | Delete course (instructor only)     |

### **IV. Enrollment Endpoints**

| **Endpoint**             | **Method** | **Description**             |
| ------------------------ | ---------- | --------------------------- |
| `/api/enroll/:courseId`  | POST       | Enroll in course            |
| `/api/enroll/my-courses` | GET        | Get user's enrolled courses |

### **V. Module Endpoints**

| **Endpoint**               | **Method** | **Description**      |
| -------------------------- | ---------- | -------------------- |
| `/api/courses/:id/modules` | GET        | Get course modules   |
| `/api/courses/:id/modules` | POST       | Add module to course |
| `/api/modules/:id`         | PUT        | Update module        |
| `/api/modules/:id`         | DELETE     | Delete module        |

---

## **6. Conclusion**

**LearnX LMS** uses secure authentication and role-based authorization to provide:

- Clear separation of **Instructor** and **Student** views
- Safe and scalable system
- Ready for future features like progress tracking and payments
