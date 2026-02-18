# 🌐 AGGREGATES – TOURISM APP

This document details the **Aggregates, Entities, and Value Objects** for the Cape Verde Tourism App, based on the previously defined Bounded Contexts.

---

## 1️⃣ User Management Context ✅

**Aggregate:** `UserAggregate`

**Entities:**

- `User` → represents the application user
- `Profile` → personal details, preferences
- `LoginAttempt` → tracks login attempts for security

**Value Objects:**

- `Email` → validated email address
- `Password` → hashed password
- `Name` → first and last name

**Domain Events:**

- `UserRegistered`
- `UserLoggedIn`
- `PasswordResetRequested`

---

## 2️⃣ Catalog Context ✅

**Aggregate:** `TripAggregate`

**Entities:**

- `Destination` → island, location, overview
- `Trip` → package including destination, duration, price
- `Review` → user feedback on trips

**Value Objects:**

- `Price` → currency and amount
- `Duration` → number of days/nights
- `Rating` → numeric rating (0–5)
- `Location` → coordinates or textual location
- `Image` → URL or resource reference

**Domain Events:**

- `TripCreated`
- `TripUpdated`
- `ReviewAdded`

---

## 3️⃣ Booking & Payment Context ✅

**Aggregates:** `BookingAggregate`, `PaymentAggregate`

**Entities:**

- `Booking` → reservation details
- `Payment` → payment transaction
- `Invoice` → generated PDF invoice
- `CartItem` → items selected before confirmation

**Value Objects:**

- `DateRange` → start and end dates
- `Money` → amount and currency
- `Participant` → traveler information
- `PaymentStatus` → enum (Pending, Paid, Failed)

**Domain Events:**

- `BookingConfirmed`
- `PaymentSucceeded`
- `PaymentFailed`
- `CartLocked`

---

## 4️⃣ Admin / Back-office Context ⚡

**Aggregate:** `AdminAggregate`

**Entities:**

- `Admin` → administrator account
- `PromoCode` → discounts and promotions
- `LogEntry` → audit logs
- `BookingStatus` → reservation status tracking

**Value Objects:**

- `Date` → timestamp
- `UsageLimit` → number of times a promo can be used

**Domain Events:**

- `PromoCodeCreated`
- `BookingStatusUpdated`
- `SecurityAlert`

---

## 5️⃣ Marketing & Loyalty Context 💡

**Aggregates:** `LoyaltyAggregate`, `ReviewAggregate`

**Entities:**

- `Review` → user trip reviews
- `LoyaltyAccount` → tracks points
- `NewsletterSubscription` → email subscription info

**Value Objects:**

- `Points` → loyalty points
- `CommentText` → review content
- `Rating` → numeric rating (0–5)

**Domain Events:**

- `ReviewSubmitted`
- `PointsCredited`
- `NewsletterSubscribed`

---

## 6️⃣ AI & Recommendation Context 💡

**Aggregate:** `RecommendationAggregate`

**Entities:**

- `Recommendation` → suggested trips
- `ChatSession` → AI chatbot interaction per user

**Value Objects:**

- `UserPreferences` → preferred trip types, locations, activities
- `Budget` → user budget range
- `TravelType` → type of travel (leisure, adventure, etc.)

**Domain Events:**

- `RecommendationGenerated`
- `ChatAnswered`
- `DynamicPricingUpdated`

---

💡 **Implementation Tips:**

1. Aggregates define **transaction boundaries**. Only one aggregate should be modified per transaction.
2. Entities are **mutable objects with identity**. Value Objects are **immutable and validated**.
3. Use **Domain Events** to communicate between contexts, e.g., `BookingConfirmed` → `PointsCredited`.
4. Aggregates can map to **modules or microservices** in your architecture.
