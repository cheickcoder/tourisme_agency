# 🌐 BOUNDED CONTEXTS – TOURISM APP

This document describes the **Bounded Contexts** of the Cape Verde Tourism App, their responsibilities, and related User Stories (US).  
The app will support **English, French, and Portuguese**. Users can select their preferred language.

---

## 1️⃣ User Management Context ✅

**Purpose:** Handles all user-related operations: authentication, profiles, and account management.  

**Key Entities & Aggregates:**  
- **Aggregates:** UserAggregate  
- **Entities:** User, Profile, LoginAttempt  
- **Value Objects:** Email, Password, Name  

**User Stories (US) Examples:**  
- US1 ✅ Email/password signup  
- US2 ✅ Secure login  
- US3 ✅ Forgot password  
- US4 ✅ User profile creation  

**Notes:**  
- Enforces security rules (password policy, login attempt limits)  
- Sends confirmation emails and notifications  
- Domain Events: `UserRegistered`, `UserLoggedIn`, `PasswordResetRequested`

---

## 2️⃣ Catalog Context ✅

**Purpose:** Manages trips, destinations, reviews, and interactive maps.  

**Key Entities & Aggregates:**  
- **Aggregates:** TripAggregate  
- **Entities:** Destination, Trip, Review  
- **Value Objects:** Price, Duration, Rating, Location, Image  

**User Stories (US) Examples:**  
- US5 ✅ CRUD destinations (Admin)  
- US6 ✅ Display trip list  
- US7 ✅ Trip detail page  
- US8 ✅ Filters & sorting  
- US9 ⚡ Interactive map  

**Notes:**  
- Must support responsive UI for web and mobile  
- Domain Events: `TripCreated`, `TripUpdated`, `ReviewAdded`

---

## 3️⃣ Booking & Payment Context ✅

**Purpose:** Handles bookings, availability checks, payments, invoices, and cart management.  

**Key Entities & Aggregates:**  
- **Aggregates:** BookingAggregate, PaymentAggregate  
- **Entities:** Booking, Payment, Invoice, CartItem  
- **Value Objects:** DateRange, Money, Participant, PaymentStatus  

**User Stories (US) Examples:**  
- US10 ✅ Multi-step booking  
- US11 ✅ Real-time availability  
- US12 ✅ Secure Stripe payment  
- US13 ✅ Automatic PDF invoice  
- US14 ✅ Booking confirmation email  
- US15 ✅ Cart lock 15 min  

**Notes:**  
- Ensures transactional consistency within aggregates  
- Domain Events: `BookingConfirmed`, `PaymentSucceeded`, `PaymentFailed`, `CartLocked`

---

## 4️⃣ Admin / Back-office Context ⚡

**Purpose:** Provides admin functionalities: dashboards, booking management, promo codes, and logs.  

**Key Entities & Aggregates:**  
- **Aggregates:** AdminAggregate  
- **Entities:** Admin, PromoCode, LogEntry, BookingStatus  
- **Value Objects:** Date, UsageLimit  

**User Stories (US) Examples:**  
- US16 ✅ Admin dashboard  
- US17 ✅ Booking management  
- US18 ⚡ Promo codes management  
- US19 ⚡ Logs & security audit  
- US20 ⚡ Performance optimization  

**Notes:**  
- Domain Events: `PromoCodeCreated`, `BookingStatusUpdated`, `SecurityAlert`  
- Enforces access control for admin operations

---

## 5️⃣ Marketing & Loyalty Context 💡

**Purpose:** Handles customer reviews, loyalty programs, newsletter subscriptions, and mobile experience.  

**Key Entities & Aggregates:**  
- **Aggregates:** LoyaltyAggregate, ReviewAggregate  
- **Entities:** Review, LoyaltyAccount, NewsletterSubscription  
- **Value Objects:** Points, CommentText, Rating  

**User Stories (US) Examples:**  
- US21 ⚡ Post-trip reviews  
- US22 ⚡ Review moderation  
- US23 ⚡ Newsletter & email marketing  
- US24 💡 Loyalty program  
- US25 ✅ Advanced mobile responsiveness  

**Notes:**  
- Domain Events: `ReviewSubmitted`, `PointsCredited`, `NewsletterSubscribed`  

---

## 6️⃣ AI & Recommendation Context 💡

**Purpose:** Provides AI-powered trip recommendations, chatbot interaction, and dynamic pricing.  

**Key Entities & Aggregates:**  
- **Aggregates:** RecommendationAggregate  
- **Entities:** Recommendation, ChatSession  
- **Value Objects:** UserPreferences, Budget, TravelType  

**User Stories (US) Examples:**  
- US26 ✅ Smart recommendation  
- US27 ⚡ AI chatbot  
- US28 💡 Dynamic pricing  

**Notes:**  
- Domain Events: `RecommendationGenerated`, `ChatAnswered`, `DynamicPricingUpdated`  
- Works across contexts (e.g., BookingConfirmed triggers PointsCredited in Loyalty context)

---

**Tip:** Each context can be implemented as a **module or microservice**, enforcing boundaries and minimizing cross-context dependencies.
