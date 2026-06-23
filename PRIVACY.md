# VEIL Privacy Policy & Principles

## Privacy First
Privacy is not an afterthought in VEIL.

It is a core design requirement.

VEIL is designed to understand behavioral patterns without accessing user content.

---

# Fundamental Principle

> VEIL stores how you interact, not what you interact with.
The system focuses on behavioral metadata rather than personal information.

---

# Explicit Consent
VEIL operates only after obtaining user consent.

Users must explicitly choose to:

- Enable collection
- Begin enrollment
- Train behavioral models

Data collection never starts automatically.

---

# What VEIL Does Not Collect
VEIL does not store:

- Passwords
- Emails
- Messages
- Documents
- Browser content
- Screenshots
- Screen recordings
- Clipboard contents
- Sensitive personal information

The system is not designed for surveillance.

---

# What VEIL Collects
Behavioral metadata only.

Examples:

### Keyboard

- Key hold duration
- Flight time
- Pause duration
- Backspace frequency

### Mouse

- Movement speed
- Curvature
- Click frequency
- Scroll behavior

### Session Metadata

- Interaction timing
- Activity rhythm
- Behavioral consistency

---

# Local Processing
The preferred architecture is local-first.

Processing occurs on the user's device whenever possible.

Benefits:

- Reduced privacy risk
- Lower exposure surface
- Increased user trust

---

# Data Ownership
Users own their behavioral data.

Users can:

- View collected data
- Export collected data
- Delete collected data
- Retrain profiles
- Disable collection

At any time.

---

# Data Retention
VEIL minimizes stored information.

Recommended approach:

```
Raw Events
      ↓
Feature Extraction
      ↓
Feature Storage
      ↓
Raw Event Removal
```

The system should retain only information necessary for authentication.

---

# Security Controls
Stored data should be protected using:

- Encryption at rest
- Secure local storage
- Access controls
- Audit logging

Future enterprise deployments should support:

- End-to-end encryption
- Hardware-backed key storage
- Secure enclaves

---

# Machine Learning Privacy
Behavioral models learn patterns rather than content.

Example:

VEIL learns:

```
Average key hold time
Average typing rhythm
Mouse movement characteristics
```

VEIL does not learn:

```
Bank passwords
Messages
Documents
Private conversations
```

---

# Transparency
Users should always know:

- What data is collected
- Why it is collected
- How it is processed
- How long it is retained

VEIL should provide clear visibility into all behavioral data stored on the device.

---

# Ethical Commitment
VEIL is intended to improve security while preserving privacy.

The project rejects:

- Covert monitoring
- Hidden surveillance
- Unauthorized collection
- Content inspection

The objective is continuous authentication, not user tracking.

---

# Our Commitment
VEIL will always prioritize:

1. User Consent
2. Transparency
3. Data Minimization
4. Local Processing
5. User Control
6. Security by Design
7. Privacy by Default

Security should not require sacrificing privacy.