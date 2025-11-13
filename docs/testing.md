# **Testing Plan**

## **1. Registration Tests**

| **TC-ID**  | **Scenario**        | **Test Steps**                              | **Expected**                                  |
| ---------- | ------------------- | ------------------------------------------- | --------------------------------------------- |
| **REG-01** | Student Register    | 1. Fill valid student data<br>2. Submit     | Account created, redirect to dashboard        |
| **REG-02** | Instructor Register | 1. Fill valid instructor data<br>2. Submit  | Account created, redirect to instructor panel |
| **REG-03** | Duplicate Email     | 1. Use existing email<br>2. Submit          | Error: "Email already exists"                 |
| **REG-04** | Invalid Email       | 1. Enter "invalid-email"<br>2. Submit       | Validation error                              |
| **REG-05** | Weak Password       | 1. Enter "123"<br>2. Submit                 | Password requirements error                   |
| **REG-06** | Empty Fields        | 1. Leave required fields empty<br>2. Submit | Field validation errors                       |
| **REG-07** | Long Inputs         | 1. Enter 255 char email<br>2. Submit        | Input length validation                       |
| **REG-08** | Special Chars       | 1. Use symbols in name<br>2. Submit         | Input sanitization works                      |

---

## **2. Login Tests**

| **TC-ID**    | **Scenario**      | **Test Steps**                                        | **Expected**                        |
| ------------ | ----------------- | ----------------------------------------------------- | ----------------------------------- |
| **LOGIN-01** | Student Login     | 1. Valid credentials<br>2. Submit                     | JWT received, student dashboard     |
| **LOGIN-02** | Instructor Login  | 1. Valid credentials<br>2. Submit                     | JWT received, instructor panel      |
| **LOGIN-03** | Wrong Password    | 1. Valid email + wrong password<br>2. Submit          | Error: "Invalid credentials"        |
| **LOGIN-04** | Non-existent User | 1. Unknown email<br>2. Submit                         | Error: "Invalid credentials"        |
| **LOGIN-05** | Empty Credentials | 1. Leave fields blank<br>2. Submit                    | Validation errors                   |
| **LOGIN-06** | Session Expiry    | 1. Wait for token expiry<br>2. Access protected route | Auto-logout, redirect to login      |
| **LOGIN-07** | Case Sensitivity  | 1. Email with different case<br>2. Submit             | Login successful (case insensitive) |

---

## **3. Authorization Tests**

| **TC-ID**   | **Scenario**                | **Test Steps**                                        | **Expected**            |
| ----------- | --------------------------- | ----------------------------------------------------- | ----------------------- |
| **AUTH-01** | Student Access              | 1. Login as student<br>2. Access student routes       | Access granted          |
| **AUTH-02** | Instructor Access           | 1. Login as instructor<br>2. Access instructor routes | Access granted          |
| **AUTH-03** | Student → Instructor Routes | 1. Login as student<br>2. Access instructor routes    | Access denied (403)     |
| **AUTH-04** | Unauthenticated Access      | 1. No login<br>2. Access protected routes             | Redirect to login (401) |

---

## **4. Test Implementation Notes**
### I. Frontend Unit Tests
- Form validation
- UI state management
- Component rendering

### II. Integration Tests
- API calls with mock responses
- End-to-end user flows
- Error handling

### IV. Test Data
```javascript
const testUsers = {
  student: {
    email: "student@test.com",
    password: "123456",
    },
  instructor: { 
    email: "instructor@test.com", 
    password: "123456" 
    },
};
```