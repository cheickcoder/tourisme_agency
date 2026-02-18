# 🌐 DOMAIN & APPLICATION SERVICES – TOURISM APP

This document describes all **Domain Services** and **Application Services** for the Cape Verde Tourism App.  
These services handle **business logic that doesn’t belong to a single entity** and orchestrate actions between aggregates or contexts.

---

## 1️⃣ User Management Context ✅

### Domain Services

| Service                    | Responsibility                                             |
| -------------------------- | ---------------------------------------------------------- |
| `AuthenticationService`    | Handles login, JWT generation, and session management      |
| `PasswordService`          | Validates, hashes, and resets passwords                    |
| `EmailConfirmationService` | Sends account confirmation emails and password reset links |

---

## 2️⃣ Catalog Context ✅

### Domain Services

| Service         | Responsibility                                  |
| --------------- | ----------------------------------------------- |
| `TripService`   | Handles creation, update, and deletion of trips |
| `ReviewService` | Validates and adds reviews, updates trip rating |
| `FilterService` | Applies price, duration, and popularity filters |

---

## 3️⃣ Booking & Payment Context ✅

### Domain Services

| Service               | Responsibility                                                              |
| --------------------- | --------------------------------------------------------------------------- |
| `BookingService`      | Manages multi-step booking process, cart locking, and availability checks   |
| `PaymentService`      | Handles Stripe integration, payment validation, retries, and status updates |
| `InvoiceService`      | Generates and sends PDF invoices after successful booking                   |
| `AvailabilityService` | Checks real-time availability for trips and participants                    |

---

## 4️⃣ Admin / Back-office Context ⚡

### Domain Services

| Service                    | Responsibility                                                  |
| -------------------------- | --------------------------------------------------------------- |
| `AdminDashboardService`    | Aggregates metrics for sales, revenue, and popular destinations |
| `BookingManagementService` | Updates booking statuses, cancels or refunds reservations       |
| `PromoCodeService`         | Creates, updates, and invalidates promo codes                   |
| `AuditLogService`          | Tracks admin actions and critical security events               |

---

## 5️⃣ Marketing & Loyalty Context 💡

### Domain Services

| Service                   | Responsibility                                            |
| ------------------------- | --------------------------------------------------------- |
| `ReviewModerationService` | Approves or removes flagged reviews                       |
| `LoyaltyService`          | Credits points after booking, manages redemption rules    |
| `NewsletterService`       | Handles subscription, unsubscription, and GDPR compliance |
| `MobileExperienceService` | Ensures responsive and adaptive mobile navigation         |

---

## 6️⃣ AI & Recommendation Context 💡

### Domain Services

| Service                 | Responsibility                                                                |
| ----------------------- | ----------------------------------------------------------------------------- |
| `RecommendationService` | Generates personalized trip suggestions based on user history and preferences |
| `ChatbotService`        | Processes user questions and returns AI-based responses                       |
| `DynamicPricingService` | Adjusts trip prices based on seasonality, demand, and user profiles           |

---

## 💡 Implementation Notes

1. **Domain Services** contain **pure business logic** that spans multiple aggregates within a context.
2. **Application Services** orchestrate **cross-context workflows**, e.g., `BookingConfirmed` triggers `PointsCredited` in Loyalty context.
3. Services can communicate via **synchronous calls or events** depending on architecture (monolith vs microservices).
4. Each service should have **clear boundaries**, be **unit-testable**, and avoid holding state.
5. Services often rely on **repositories and value objects** for data access and validation.
