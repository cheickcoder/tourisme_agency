# 🌐 DOMAIN EVENTS – TOURISM APP

This document lists all **Domain Events** for the Cape Verde Tourism App.  
Domain Events represent **important occurrences in the domain** that other parts of the system may react to.

---

## 1️⃣ User Management Context ✅

| Event                    | Trigger / Description                                                      |
| ------------------------ | -------------------------------------------------------------------------- |
| `UserRegistered`         | Triggered after a successful signup; used to send confirmation email       |
| `UserLoggedIn`           | Triggered after successful login; used for analytics and security tracking |
| `PasswordResetRequested` | Triggered when a user requests a password reset; sends email link          |

---

## 2️⃣ Catalog Context ✅

| Event         | Trigger / Description                                                       |
| ------------- | --------------------------------------------------------------------------- |
| `TripCreated` | Triggered when admin adds a new trip; notifies catalog services             |
| `TripUpdated` | Triggered after modifying trip details; updates caches and frontends        |
| `ReviewAdded` | Triggered when a user submits a review; may affect trip rating calculations |

---

## 3️⃣ Booking & Payment Context ✅

| Event              | Trigger / Description                                                                      |
| ------------------ | ------------------------------------------------------------------------------------------ |
| `BookingConfirmed` | Triggered after reservation is successfully confirmed; may trigger loyalty points or email |
| `PaymentSucceeded` | Triggered after a successful payment; generates invoice PDF                                |
| `PaymentFailed`    | Triggered when payment fails; notifies user and may unlock cart                            |
| `CartLocked`       | Triggered when a user adds items to cart; locks them for 15 minutes                        |

---

## 4️⃣ Admin / Back-office Context ⚡

| Event                  | Trigger / Description                                                            |
| ---------------------- | -------------------------------------------------------------------------------- |
| `PromoCodeCreated`     | Triggered when admin creates a new promo code; available immediately in system   |
| `BookingStatusUpdated` | Triggered when admin changes a booking status (Confirmed / Cancelled / Refunded) |
| `SecurityAlert`        | Triggered for suspicious activity in admin actions; logs alert for audit         |

---

## 5️⃣ Marketing & Loyalty Context 💡

| Event                  | Trigger / Description                                                   |
| ---------------------- | ----------------------------------------------------------------------- |
| `ReviewSubmitted`      | Triggered when a user submits a review; may notify admin for moderation |
| `PointsCredited`       | Triggered after successful booking; adds points to user loyalty account |
| `NewsletterSubscribed` | Triggered when a user subscribes to newsletter; confirmation email sent |

---

## 6️⃣ AI & Recommendation Context 💡

| Event                     | Trigger / Description                                                            |
| ------------------------- | -------------------------------------------------------------------------------- |
| `RecommendationGenerated` | Triggered when AI generates personalized trip recommendations for a user         |
| `ChatAnswered`            | Triggered when AI chatbot responds to a user question                            |
| `DynamicPricingUpdated`   | Triggered when AI adjusts trip prices based on seasonality, demand, or user data |

---

💡 **Implementation Notes:**

1. **Event-driven architecture:** Domain Events can trigger **cross-context actions**, e.g., `BookingConfirmed` → `PointsCredited` in Loyalty context.
2. **Immutability:** Once raised, events should **not be modified**.
3. **Persistence:** Events can be stored for **audit logs, replay, or integration**.
4. **Messaging:** Can be implemented via **message bus, Kafka, or event queues** between services or modules.
