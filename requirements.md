# Project Requirements: Pehchaan

## 1. Project Overview
**Pehchaan** is a voice-first, AI-powered digital ledger designed to bridge the gap between the informal economy and formal financial systems. It allows blue-collar workers (artisans, laborers, service providers) to document their daily work through voice notes and images, creating a verifiable "Proof-of-Work" history.

## 2. Problem Statement
Informal workers lack documentation (salary slips, employment contracts), leading to:
* Inability to access formal credit or loans.
* Exclusion from government grants.
* Limited market visibility and career mobility.

## 3. User Personas
* **The Worker (Primary):** Low digital literacy, speaks local dialect, relies on daily wages. Needs a low-friction way to record earnings.
* **The Verifier (Secondary):** Banks, MFIs (Micro-Finance Institutions), or Employers who need to verify the worker's consistency and skill level.

## 4. Functional Requirements

### 4.1. Input Module (The "Low-Friction" Interface)
* **Voice Logging:** Users must be able to record work details (e.g., "Painted 2 walls today, earned ₹800") in their native language (Hindi/Hinglish/Regional).
* **Visual Evidence:** Users must be able to upload a photo of the finished work or raw materials.
* **Location Tagging:** System should capture approximate location (if available) to validate work context.

### 4.2. Processing Module (The "AI Brain")
* **Multilingual ASR:** Convert vernacular speech to text with high accuracy using **Amazon Transcribe**.
* **Image Analysis:** Analyze uploaded photos using **Amazon Rekognition** to identify objects, tools, or finished goods.
* **Cross-Verification (GenAI):** Use **Amazon Bedrock (Claude 3)** to compare the transcript with the image.
  * *Rule:* If the user says "I made a wooden chair" but the image shows a "Steel Gate," flag as `Unverified`.
* **Anomaly Detection:** Flag unrealistic claims (e.g., claiming 24 hours of work in a single day).

### 4.3. Output Module (The "Value Add")
* **Work History Ledger:** Display a chronological list of verified jobs.
* **Digital CV Generation:** Generate a downloadable PDF summary of skills and past projects.
* **Credit Consistency Score:** Calculate a simple 0-100 score based on frequency of work and verified income.

## 5. Non-Functional Requirements
* **Latency:** Voice processing and verification response should take < 10 seconds.
* **Accessibility:** UI must support high-contrast and voice-guided navigation.
* **Connectivity:** System must handle intermittent internet (store-and-forward architecture).
* **Data Privacy:** User data (voice/images) must be stored securely and not shared without consent.
* **Scalability:** Architecture must support serverless scaling to handle spikes in traffic.

## 6. Constraints
* **Hardware:** Must run effectively on low-end Android devices or via WhatsApp Business API.
* **Cost:** Operational cost per user transaction must be kept minimal (Serverless optimization).
