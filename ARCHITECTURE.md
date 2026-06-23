# VEIL Architecture

## Overview
VEIL (Behavioral Intelligence Authentication Layer) is a privacy-first continuous authentication system that verifies identity using behavioral biometrics.

Instead of trusting a user only during login, VEIL continuously evaluates behavioral signals throughout a session and calculates a dynamic trust score.

---

# High-Level Architecture

```
┌─────────────────────┐
│ User Interaction    │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Event Collector     │
│ (Keyboard/Mouse)    │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Feature Extraction  │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Feature Store       │
│ (SQLite/Postgres)   │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Behavioral Models   │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Risk Engine         │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Response Layer      │
└─────────────────────┘
```

---

# Core Components

## 1. Event Collector
The collector runs locally and gathers behavioral metadata from user interactions.

Captured signals include:

### Keyboard

- Key hold duration
- Flight time between keys
- Typing rhythm
- Backspace frequency
- Pause duration

### Mouse

- Movement speed
- Cursor acceleration
- Trajectory curvature
- Click frequency
- Scroll behavior

The collector never stores typed content.

---

## 2. Feature Extraction Engine
Raw events are transformed into machine-learning-ready features.

Example:

Raw Events:

```
Press A
Release A
Move Mouse
Scroll
```

Generated Features:

```
{
  "avg_hold_time": 102,
  "avg_flight_time": 76,
  "mouse_speed": 341,
  "scroll_rate": 5.4
}
```

Features are generated in fixed time windows.

---

## 3. Feature Store
Stores extracted behavioral features.

Initial implementation:

- SQLite

Future implementation:

- PostgreSQL
- Distributed storage

The database stores feature vectors rather than raw interaction content.

---

## 4. Behavioral Models
VEIL primarily uses anomaly detection.

Initial models:

- Isolation Forest
- One-Class SVM

Purpose:

Learn normal user behavior and identify deviations.

VEIL focuses on:

```
What is normal?
```
rather than
```
Who is this user?
```

This allows effective operation with limited training data.

---

## 5. Risk Engine
Model outputs are converted into a normalized risk score.

Example:

```
Risk = 12%
```

```
Risk = 84%
```

Risk scores are continuously updated throughout the session.

---

## 6. Security Response Layer
Actions depend on risk level.

Risk | Action
---|---
0-30 | Allow
30-60 | Monitor
60-80 | Re-authenticate
80-100 | Restrict Session

---

# Context-Aware Profiles
Future versions support multiple behavioral profiles.

```
User
├── Normal
├── Tired
├── Focused
├── Mobile
└── Desktop
```

This reduces false positives caused by natural behavioral variation.

---

# Adaptive Learning
Model updates occur only during high-confidence sessions.

This prevents attackers from poisoning behavioral profiles.

Training Conditions:

- Low risk score
- High confidence
- Verified session

---

# Multi-Factor Fusion
Future trust calculations combine:

- Behavioral Biometrics
- Device Fingerprint
- Environmental Context
- Traditional Authentication

Final output:

```
Trust Score = 94%
Risk Score = 6%
```

---

# Design Principles

- Privacy First
- Local Processing
- Explainable AI
- Continuous Authentication
- Adaptive Security
- User-Controlled Data