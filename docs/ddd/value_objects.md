# 🌐 VALUE OBJECTS – TOURISM APP

This document lists all **Value Objects** for the Cape Verde Tourism App.  
Value Objects are **immutable, validated, and represent domain concepts** without identity.

---

## 1️⃣ User Management Context ✅

| Value Object | Description         | Validation / Rules                                                  |
| ------------ | ------------------- | ------------------------------------------------------------------- |
| `Email`      | User email address  | Must be valid email format; unique per user                         |
| `Password`   | User password       | Min 8 characters; hashed; strong policy (letters, numbers, symbols) |
| `Name`       | First and last name | Non-empty; max 50 characters each                                   |

---

## 2️⃣ Catalog Context ✅

| Value Object | Description                  | Validation / Rules                                           |
| ------------ | ---------------------------- | ------------------------------------------------------------ |
| `Price`      | Trip cost                    | Positive decimal; currency specified                         |
| `Duration`   | Trip length                  | Positive integer (number of days/nights)                     |
| `Rating`     | User or trip rating          | Numeric 0–5; optional decimal                                |
| `Location`   | Trip or destination location | Must include coordinates (lat/lon) or validated text address |
| `Image`      | Image reference              | Valid URL or storage reference                               |

---

## 3️⃣ Booking & Payment Context ✅

| Value Object    | Description                    | Validation / Rules                                |
| --------------- | ------------------------------ | ------------------------------------------------- |
| `DateRange`     | Start and end dates of booking | Start < End; cannot be past dates                 |
| `Money`         | Payment amount                 | Positive decimal; currency required               |
| `Participant`   | Traveler info                  | Name, email, optional age; validated email format |
| `PaymentStatus` | Payment state                  | Enum: Pending, Paid, Failed; default Pending      |

---

## 4️⃣ Admin / Back-office Context ⚡

| Value Object | Description                  | Validation / Rules                             |
| ------------ | ---------------------------- | ---------------------------------------------- |
| `Date`       | Timestamp of logs or events  | ISO 8601 format; immutable                     |
| `UsageLimit` | Maximum usage of promo codes | Positive integer; cannot exceed business limit |

---

## 5️⃣ Marketing & Loyalty Context 💡

| Value Object  | Description    | Validation / Rules                                          |
| ------------- | -------------- | ----------------------------------------------------------- |
| `Points`      | Loyalty points | Non-negative integer; cannot exceed max allowed per program |
| `CommentText` | Review content | Non-empty; max 500 characters                               |
| `Rating`      | Review rating  | Numeric 0–5; optional decimal                               |

---

## 6️⃣ AI & Recommendation Context 💡

| Value Object      | Description             | Validation / Rules                                                           |
| ----------------- | ----------------------- | ---------------------------------------------------------------------------- |
| `UserPreferences` | User travel preferences | Must include categories (beach, adventure, cultural); optional subcategories |
| `Budget`          | User budget range       | Positive decimal min and max; min ≤ max                                      |
| `TravelType`      | Type of travel          | Enum: Leisure, Adventure, Family, Romantic, Cultural                         |

---

💡 **Implementation Notes:**

1. **Immutability:** Value Objects should not be changed after creation.
2. **Validation:** Ensure all constraints are enforced on creation.
3. **Comparison:** Two Value Objects with the same properties are considered **equal**.
4. **Usage:** Used inside Aggregates, Entities, or as parameters in Domain Services.
5. **Serialization:** Must support storage in DB and transmission via API (JSON, etc.).
