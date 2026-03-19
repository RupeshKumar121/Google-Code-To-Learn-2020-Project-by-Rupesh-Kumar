# 🚨 Rakshak — Road Safety App

> **A multipurpose road safety application that automatically detects accidents and instantly alerts nearby people to save lives.**

---

## 📖 About

Rakshak is an Android application built to tackle one of India's most critical issues — road accident deaths. With over **1,51,417 road accident deaths in India in 2018** alone, and nearly **30% caused by delayed ambulance response**, Rakshak aims to bridge the gap between an accident and help arriving on time.

When an accident is detected, the app instantly notifies all registered users within a **1 km radius** of the accident spot, sharing the exact location and victim details — so bystanders can respond or call an ambulance immediately.

Built using **MIT App Inventor**, with a custom PHP + MySQL backend server for real-time location and user data.

---

## 🧠 How Accident Detection Works

The app monitors vehicle speed continuously using the device's sensors. An accident event is triggered when:

1. The vehicle speed **exceeds 50 km/hr**
2. Within **3 seconds**, the speed drops to **below 5 km/hr**

This sudden deceleration is treated as a collision. On detection:
- A **push notification** is sent to all registered users within 1 km
- An **SMS** is sent to the user's emergency contacts
- The exact **accident location** is shared

---

## ✨ Features

### 🔐 Login & Registration
- User account creation with credentials (Name, Username, Driving Licence, State, etc.)
- **OTP verification** on registration
- Firebase DB used to store and verify credentials

### 🏠 Home Screen
- Central hub to navigate all features
- Continuously updates and stores the user's live location on the server for nearby-accident detection
- Location is **not tracked historically** — only current position is stored

### 🚗 Drive Screen
- Displays real-time **vehicle speed**, **distance travelled**, and **current location on map**
- **Proximity Sensor** support — screen goes black when device is in pocket, but all functions keep running
- **Auto-mutes incoming calls** while driving and sends an auto-reply SMS to the caller
- Caller's number is saved in the Notification Screen for later
- **Park feature** — saves vehicle's parked location, viewable in the Vehicles Screen
- Triggers accident detection logic automatically

### 🔔 Notification Screen
- Stores all alerts: nearby accident notifications, missed call alerts while driving
- Displays accident location and victim details when a nearby accident is detected

### 📄 Storage
- Fully sync-able cloud storage for personal vehicle documents (Driving Licence, RC book, etc.)
- Documents can be uploaded and accessed anytime for police verification
- File upload powered by the **Pura Vida Apps File module** — [puravidaapps.com/postfile.php](https://puravidaapps.com/postfile.php)

### 🚘 Vehicles Screen
- Register multiple vehicles (brand, number, etc.)
- Select active vehicle before driving
- View parked vehicle location on the map

### 🆘 Emergency Contacts
- Add phone numbers that receive an automatic SMS during an accident event

### 📚 Safety Book
- In-app road safety rules and guidelines to promote safe driving habits

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| App Development | MIT App Inventor |
| Backend Server | PHP (hosted on 000webhost) |
| Database | MySQL + Firebase DB |
| Location | GPS Location Sensor |
| Speed Detection | Pedometer |
| Proximity | Proximity Sensor |
| Notifications | Firebase Push Notifications |
| Messaging | Android Texting Component |
| Maps | Google Maps via Activity Starter |
| Call Muting | Taifun Settings Extension (Android 7 and below) |
| File Storage | [Pura Vida Apps — Post File Extension](https://puravidaapps.com/postfile.php) |

---

## 🗄️ Backend — PHP Files

Two PHP scripts power the server side:

**`database.php`** — Manages user location records
- `create` — Registers a new user's location in the database
- `update` — Updates the user's current latitude/longitude in real time

**`nearpeople.php`** — Finds nearby users
- Takes the accident's latitude/longitude as input
- Queries all users within **1 km** using a custom `twopoints_on_earth()` MySQL function
- Returns a list of nearby registered usernames to notify

---

## 📱 App Screens Overview

| Screen | Purpose |
|---|---|
| Screen 1 (Splash) | Logo screen; redirects to Login or Home based on session |
| Login Screen | Authenticates user via Firebase DB |
| Register Screen | New user registration with OTP verification |
| Home Screen | Navigation hub + live location tracking |
| Drive Screen | Speed monitoring, accident detection, proximity sensor |
| Notification Screen | Stores accident alerts and missed call logs |
| Safety Book | Road safety rules and awareness |
| Storage | Vehicle document upload and sync |
| Vehicles Screen | Register vehicles and view parked location |
| Emergency Phone Screen | Manage emergency contact numbers |

---

## 💡 Key Innovations

- **Passive accident detection** — no manual input needed while driving
- **Phone as a helper, not a distraction** — proximity sensor and auto-mute ensure the device is safe to use while driving
- **Hyperlocal alerts** — only people within 1 km are notified, ensuring relevant, actionable responses
- **Future scope** — end-to-end encryption of location data, accurate nationwide accident data collection for research

---

## 📄 License

This project was built for educational and social impact purposes. All rights reserved by Rupesh Kumar.
