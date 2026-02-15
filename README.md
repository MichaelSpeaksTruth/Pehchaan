# 🇮🇳 Pehchaan (पहचान)

> **Giving Identity to the Invisible Workforce.**  
> *An AI-powered "Proof-of-Work" ledger for India's informal economy.*

[![AWS](https://img.shields.io/badge/Built%20on-AWS-orange?logo=amazon-aws&style=for-the-badge)](https://aws.amazon.com/)
[![AI for Bharat](https://img.shields.io/badge/Hackathon-AI%20for%20Bharat-blue?style=for-the-badge)](https://github.com/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)]()

---

## 🗣️ "Meri Awaaz, Meri Pehchaan" (My Voice, My Identity)

Millions of skilled workers in India—carpenters, farmers, artisans—work hard every day but remain **invisible** to the formal financial system. They have no salary slips, no LinkedIn profiles, and consequently, **no access to credit.**

**Pehchaan** changes that.

We are building a **Voice-First, Multimodal Ledger** that allows workers to document their daily labor simply by speaking and snapping a photo. Our AI verifies this data to create a trusted "Work Credit Score."

---

## 🚀 How It Works

We turned a complex problem into a 3-step solution usable on a 2G connection:

1. **🎙️ Speak (Bolo):** The worker sends a voice note via WhatsApp/Web.
   * *"Aaj 50kg tamatar tode aur mandi mein beche."* (Harvested 50kg tomatoes today.)

2. **📸 Snap (Dekhao):** They upload a photo of the work.

3. **✅ Verify (Samjho):**
   * **AWS Transcribe** converts the dialect to text.
   * **AWS Rekognition** scans the image (e.g., detects 'Tomatoes', 'Farm').
   * **AWS Bedrock (GenAI)** Cross-verifies: *Does the image match the voice claim?*

4. **🔓 Unlock:** The worker gets a **Verified Work History** (PDF) to share with banks for loans.

---

## 🛠️ Tech Stack (The Engine)

We leveraged the power of **AWS Serverless** to keep it scalable and low-cost.

| Component | Technology | Purpose |
| :--- | :--- | :--- |
| **Brain (GenAI)** | **Amazon Bedrock (Claude 3)** | Logic, reasoning, and fraud detection. |
| **Ears (Audio)** | **Amazon Transcribe** | Speech-to-Text for Indian languages. |
| **Eyes (Vision)** | **Amazon Rekognition** | Object detection and scene analysis. |
| **Backend** | **AWS Lambda** | Serverless orchestration. |
| **Database** | **Amazon DynamoDB** | Storing the immutable work ledger. |
| **Storage** | **Amazon S3** | Securely holding user media. |

---

## 📱 Features

* **Vernacular First:** Designed for users who may not read/write, but can speak confidently.
* **Thin-File Solution:** Creates a credit history for those with "zero CIBIL score."
* **Offline Capable:** Architecture designed for intermittent connectivity in Tier-3/4 cities.
* **Portable Identity:** The "Work CV" belongs to the user, not a platform.

---

## 📸 Architecture

*(For detailed system design, check [DESIGN.md](./design.md))*

```mermaid
graph LR
    A[User (WhatsApp/Web)] -->|Voice + Image| B(API Gateway)
    B --> C{AWS Lambda}
    C -->|Audio| D[Amazon Transcribe]
    C -->|Image| E[Amazon Rekognition]
    D & E --> F[Amazon Bedrock]
    F -->|Verified/Flagged| G[(DynamoDB Ledger)]
    G --> H[Bank/Credit Portal]
```
