# **Functional Use Case - LearnX LMS**

## **1. Functional Overview**

- Secure login and registration (JWT)
- Role-based dashboards (Instructor / Student)
- Course creation, management, and enrollment
- Video upload & playback (Cloudinary)
- PWA-enabled for mobile access  

| **Module** | **Function** |
|-------------|--------------|
| **Authentication** | Secure login & registration |
| **Courses** | Create & manage course details |
| **Media** | Upload and stream videos |
| **Enrollment** | Students join courses |
| **Dashboard** | Role-based user views |

---

## **2. Functional Flow**

### **2.1 User Registration & Login**

```mermaid
flowchart TD
    A[User Opens App] --> B[Choose Sign Up or Login]
    B -->|Sign Up| C[Enter Name, Email, Password, Role]
    C --> D[System Validates & Creates Account]
    B -->|Login| E[Enter Credentials]
    E --> F[Server Verifies Credentials]
    F -->|Valid| G[Generate JWT Token]
    G --> H{User Role}
    H -->|Instructor| I[Redirect to Instructor Dashboard]
    H -->|Student| J[Redirect to Student Dashboard]
    F -->|Invalid| K[Show Error Message]
```

---

### **2.2 Video Playback Flow**

```mermaid
flowchart LR
    A[Student Opens Lesson Page] --> B[Click Lesson Tabs]
    B --> C[Stream Video in Player]
    C --> D[Mark Lesson as Completed]
```

---

### **2.3 Enrollment Flow**

```mermaid
flowchart TD
    A[Student Selects Course] --> B[Click Enroll]
    B --> C[Redirect to Payment Gateway - Test Mode]
    C --> D{Payment Successful?}
    D -->|Yes| E[Confirm Enrollment]
    D -->|No| F[Show Payment Failed Message]
    E --> G[Add Course to Student Dashboard]
    G --> H[Access Course Lessons]
```

---

## **3. Core Functional Modules**

| **Module**            | **Functionality**                               |
| --------------------- | ----------------------------------------------- |
| **Authentication**    | Register and login securely using JWT           |
| **Authorization**     | Role-based dashboard redirection                |
| **Dashboard**         | Personalized interface for each user role       |
| **Course Management** | Instructors create, edit, and delete courses    |
| **Media Management**  | Upload and watch videos using Cloudinary       |
| **Enrollment**        | Students browse and enroll in courses           |

---

## **4. Instructor & Student Workflow**

```mermaid
flowchart TD
    A[Instructor Dashboard] --> B[Create Course]
    B --> C[Add Course Details - Title, Description, Tags]
    C --> D[Upload Lesson Videos to Cloudinary]
    D --> E[Publish Course]
    E --> F[Course Visible to Students]
    F --> G[Manage Existing Courses - Edit / Delete]
    I[Student Dashboard] --> J[Browse Courses]
    J --> K[View Course Details]
    K --> L[Click Enroll]
    L --> M[Enrollment Confirmed]
    M --> N[Access Lessons]
    N --> O[Watch Videos]
```

---

## **5. Use Case Summary**

| **ID** | **Use Case**     | **Action**                          |
| :----: | ---------------- | ----------------------------------- |
|   F1   | Register User    | Sign up as Instructor or Student    |
|   F2   | Login User       | Authenticate using JWT or Firebase  |
|   F3   | Create Course    | Instructor adds course with videos  |
|   F4   | Enroll in Course | Students join a course              |
|   F5   | Watch Videos     | Students stream lessons             |
|   F6   | Manage Course    | Instructor edits or deletes courses |

---

## **6. System Flow**

```mermaid
graph LR
    A[Frontend - React/Vite] --> B[Backend - Nodejs/Express]
    B --> C[(Database - MongoDB)]
    B --> D[(Cloudinary)]
    A -->|API Calls| B
    A -->|PWA| A
```

---

## **7. Edge Case Handling**

| **Scenario**        | **Expected Behavior**              |
| ------------------- | ---------------------------------- |
| Invalid credentials | Show error message                 |
| JWT expired         | Redirect to login                  |
| Unauthorized access | Redirect to dashboard              |
| Upload failed       | Retry or notify user               |
| Video not loading   | Retry or show fallback             |

--- 

## **8. Future Scope**

* **Progress Tracker:** Track lesson completion and learning analytics
* **Payment Integration:** Enable paid course enrollment
* **AI Recommendations:** Suggest courses based on learner behavior
* **Enhanced PWA:** Push notifications, offline playback, and sync
