# SE-Lab-exam-
# 🩸 Blood Bank System — Process Blood Request Subsystem

A robust, object-oriented implementation of a **Blood Bank Request Processing System** with complete validation, inventory management, and **white-box test coverage (100%)**.

---

# 🚀 Features

* ✅ Process blood requests from hospitals
* ✅ Strong input validation (Blood Group, Units, Hospital ID)
* ✅ Inventory management with real-time updates
* ✅ Cross-match compatibility checking
* ✅ Shortage alert system
* ✅ Structured JSON responses
* ✅ Exception handling with custom hierarchy
* ✅ **White-box testing (Statement, Branch, Path coverage = 100%)**

---

# 🏗️ System Architecture

The system follows a clean layered design:

## 📦 Components

### 1. Models

* `BloodRequest`
* `BloodUnit`
* `Hospital`
* `BloodGroup (Enum)`

### 2. Services

* `BloodRequestService` → Core business logic
* `InventoryManager` → Stock management
* `CrossMatchService` → Compatibility check
* `NotificationService` → Alerts & notifications

### 3. Controller

* `BloodRequestController` → Handles requests and returns JSON responses

### 4. Exceptions

Custom exception hierarchy:

* `ValidationException`
* `InvalidBloodGroupException`
* `InvalidHospitalException`
* `InsufficientStockException`
* `IncompatibleBloodException`

---

# 🔁 Workflow (Process Blood Request)

1. Validate input request
2. Verify hospital registration
3. Validate blood group & units
4. Perform cross-match check
5. Check inventory availability
6. Allocate blood units
7. Trigger shortage alert if needed
8. Notify hospital
9. Return structured response

---

# 📥 Input Format

```json
{
  "request_id": "REQ-01",
  "blood_group": "A+",
  "units": 5,
  "hospital_id": "H-001"
}
```

---

# 📤 Output Format

### ✅ Success Response

```json
{
  "status": "SUCCESS",
  "message": "Blood units successfully allocated.",
  "allocatedUnits": 5,
  "bloodGroup": "A+",
  "hospitalId": "H-001"
}
```

### ⚠️ Success with Alert

```json
{
  "status": "SUCCESS",
  "message": "Blood units successfully allocated.",
  "allocatedUnits": 1,
  "bloodGroup": "B+",
  "hospitalId": "H-001",
  "alert": "shortage alert triggered"
}
```

### ❌ Error Response

```json
{
  "status": "ERROR",
  "message": "Invalid blood group",
  "allocatedUnits": 0,
  "bloodGroup": "X+",
  "hospitalId": "H-001"
}
```

---

# 🧪 Testing

## 1. ECP (Equivalence Class Partitioning)

Covers:

* Valid requests
* Invalid blood groups
* Invalid units
* Invalid hospital IDs
* Insufficient stock

---

## 2. BVA (Boundary Value Analysis)

| Test Case      | Description     |
| -------------- | --------------- |
| Units = 1      | Lower boundary  |
| Units = 10     | Upper boundary  |
| Units = 11     | Exceeds limit   |
| Stock == Units | Alert triggered |
| Stock < Units  | Error           |

---

## 3. White-Box Testing ✅

All independent paths are covered:

### 🔹 Path P1 (Happy Path)

* Valid input
* Stock > units

### 🔹 Path P2 (Exact Match)

* Stock == units
* Shortage alert triggered

### 🔹 Path P3 (Error Paths)

* All validation failures
* Insufficient stock

---

## 📊 Coverage Achieved

* ✅ Statement Coverage: **100%**
* ✅ Branch Coverage: **100%**
* ✅ Path Coverage: **P1, P2, P3 fully covered**

---

# ▶️ Running the Project

## Run White-Box Tests

```bash
python your_file_name.py
```

Output includes:

```
Test Case: WB-01
Path: P1

Input: {...}
Expected Output: {...}
Actual Output: {...}
Result: PASS
```

---

# 📊 Test Summary Output

```
========================================
WHITE BOX TEST SUMMARY
Total Tests: 15
Passed: 15
Failed: 0
Coverage:
- Statement Coverage: 100%
- Branch Coverage: 100%
- Path Coverage: P1, P2, P3 covered
========================================
```

---

# ⚠️ Validation Rules

### Blood Group

* Must be valid (A+, B-, etc.)
* Empty → error
* Invalid → error

### Units

* Must be integer
* ≥ 1 and ≤ 10

### Hospital ID

* Must start with `H-`
* Must exist in system

---

# 🧠 Design Highlights

* ✔ Follows **SOLID principles**
* ✔ Modular and extensible
* ✔ Clear separation of concerns
* ✔ Robust exception handling
* ✔ Fully testable architecture

---

# 📌 Future Improvements

* Add database integration
* REST API layer (Flask / FastAPI)
* Logging system
* Multi-blood allocation (cross-group sourcing)
* UI dashboard

---

# 👨‍💻 Author

Blood Bank System — Process Request Module
Designed for **reliable, test-driven backend systems**

---

# ⭐ Conclusion

This project demonstrates:

* Clean system design
* Strong validation and business logic
* Complete white-box test coverage

👉 Ready for real-world extension and deployment.
