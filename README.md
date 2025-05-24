

# sBTC-Cred 📘

**Decentralized Peer Assessment and Skill Verification on the Stacks Blockchain**

sBTC-Cred is a decentralized credentialing platform designed to verify user skills via community-driven peer assessments. It ensures transparent, immutable, and reputation-based validation of knowledge, leveraging the security and finality of the Stacks blockchain.

---

## 📜 Overview

sBTC-Cred enables users to register, request skill assessments, and participate in evaluating others. By analyzing the statistical validity of peer assessments, sBTC-Cred builds a trustable reputation system that rewards accuracy and penalizes outliers or bad actors.

---

## 🚀 Features

* 🧑‍🎓 **User Registration**
  Users register once and can then request assessments or become assessors.

* 🧠 **Skill Creation**
  Admins (contract owner) define skill categories, including metadata and number of required assessments.

* 📊 **Peer Assessment System**
  Peers score requested assessments. The system calculates the mean score and standard deviation to verify the claim and determine reward/penalty.

* 🌐 **Reputation Tracking**
  Users earn or lose reputation based on how close their assessments are to the consensus.

* 📁 **Immutable Records**
  All interactions are stored on-chain for transparency and future auditing.

---

## 📘 How It Works

### 1. User Registration

```clojure
(register-user)
```

### 2. Admin Adds Skills

```clojure
(add-skill name description required-assessments category)
```

### 3. User Requests Assessment

```clojure
(request-assessment skill-id)
```

### 4. Peer Submits Assessment

```clojure
(submit-assessment skill-id user score)
```

### 5. Finalize and Verify

```clojure
(finalize-verification skill-id)
```

---

## 📐 Reputation Logic

* **Reward (Valid assessment):** +2
* **Penalty (Invalid assessment):** -5
* **Validation Criteria:** Assessment must fall within ±15 points of the mean.
* **Assessment Validity Threshold:** Mean score ≥ 70 (out of 100)
* **Minimum Assessors Required:** 3

---

## 🧮 Internal Math

* **Mean** is computed on submitted scores.
* **Standard Deviation** checks consistency of scores.
* **Deviation-based Filtering:** Assessors are judged based on how far their scores deviate from the mean.

---

## 📁 Data Structures

### `users`

Stores registration, skill list, reputation, assessment stats.

### `skills`

Skill metadata defined by admin.

### `skill-assessments`

Tracks assessments, scores, timestamps, and verification status.

### `skill-reputation`

Skill-specific assessor statistics.

---

## 🔐 Access Control

* Only the contract owner can add skills.
* Only registered users can request or give assessments.

---

## ✅ Error Handling

| Error Code | Description           |
| ---------- | --------------------- |
| 100        | Not authorized        |
| 101        | Already registered    |
| 102        | Not registered        |
| 103        | Not enough assessors  |
| 104        | Already assessed      |
| 105        | Max assessors reached |
| 106        | Invalid score         |
| 107        | Invalid skill ID      |
| 108        | Invalid input         |

---

## 🔎 Read-Only Functions

```clojure
(get-user-details user)
(get-skill-details skill-id)
(get-assessment-details skill-id user)
(get-assessor-count skill-id user)
(get-user-reputation user)
(get-skill-specific-reputation user skill-id)
(get-assessment-statistics skill-id user)
```

---

## 🧪 Testing

Unit tests should simulate:

* User registration
* Skill creation
* Full assessment lifecycle
* Reputation updates
* Invalid score submissions

---

## 📜 License

MIT License. Open to contribution, discussion, and extension under DAO-based governance in future versions.

---
