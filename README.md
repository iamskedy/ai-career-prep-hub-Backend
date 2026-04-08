# 🚀 AI Career Prep Hub 

**Live Demo:** [Link to Live Site] | **Backend API:** [Link to Render URL] | **Video Walkthrough:** [YouTube/Loom Link]

> A Full-Stack AI platform built to revolutionize how candidates prepare for job interviews. By leveraging Google's Gemini AI, this application analyzes resumes against specific job descriptions to generate personalized mock interviews, identify skill gaps, and dynamically create tailored, ATS-friendly resumes.

---

## 💡 The Problem & Solution
**The Problem:** Job seekers often apply with generic resumes and struggle to anticipate role-specific interview questions. 
**The Solution:** An automated pipeline that acts as a personal career coach. The user uploads a standard resume and a target job description. The AI instantly provides a match score, a customized day-by-day preparation plan, and exports a freshly tailored PDF resume optimized for that specific ATS.

---

## ✨ Key Features (The "Wow" Factor)
* 🧠 **AI-Powered Analysis:** Context-aware parsing of PDF resumes mapped against live job descriptions using Google Gemini.
* 🎯 **Dynamic ATS Resume Generation:** Programmatic generation of tailored PDF resumes using Puppeteer, ensuring pixel-perfect layout and ATS readability.
* 🛡️ **Robust Security:** Secure authentication pipeline using HttpOnly cookies, JWTs, and a token-blacklisting architecture for secure session termination.
* 📊 **Structured AI Responses:** Strict enforcement of JSON schemas from the LLM to ensure reliable database storage and predictable frontend rendering.

---

## 🛠 Tech Stack & Architecture

### **Backend (Core)**
* **Runtime / Framework:** Node.js, Express.js
* **Database:** MongoDB, Mongoose (with normalized relational schemas)
* **AI Integration:** `@google/genai` (Gemini 3 Flash Preview)
* **Authentication:** JWT, bcryptjs, custom Auth Middleware
* **Validation:** Zod (Strict payload validation)
* **Deployment:** Render (Web Services)

### **Frontend (Client)**
* **Framework:** Next.js / React *(Update this based on your actual frontend tech)*
* **Styling:** Tailwind CSS
* **State Management:** Context API / Redux

### **System Design Overview**
1. **Client Layer:** Sends `multipart/form-data` containing PDF blobs and text.
2. **API Gateway (Express):** intercepts requests, validates JWT via cookies, and passes files to Multer (Memory Storage).
3. **Processing Layer:** Extracts raw text from PDF buffers.
4. **AI Layer:** Constructs highly engineered prompts and interfaces with the Gemini API to return structured JSON.
5. **Persistence Layer:** Saves the AI reports to MongoDB for historical tracking.

---

## 🚧 Technical Challenges & How I Solved Them

* **Challenge:** LLMs often return unpredictable formatting, breaking frontend rendering.
  **Solution:** Engineered strict prompt instructions and implemented server-side parsing to guarantee the AI output always matched a predefined JSON structure before saving to MongoDB.
* **Challenge:** Generating dynamic PDFs that maintain ATS readability.
  **Solution:** Bypassed standard PDF-creation libraries in favor of `Puppeteer`. I generated HTML/CSS templates dynamically on the server and used headless Chromium to print them to PDF, ensuring perfect formatting and text-layer preservation.
* **Challenge:** Securely handling user sessions without exposing tokens to XSS attacks.
  **Solution:** Transitioned from `localStorage` token management to `HttpOnly` cookies and implemented a MongoDB-backed blacklist model to handle immediate token invalidation on logout.

---

## 🚀 Local Development Setup

**1. Clone the repository**
```bash
git clone [https://github.com/iamskedy/ai-career-prep-hub-Backend.git](https://github.com/iamskedy/ai-career-prep-hub-Backend.git)
cd ai-career-prep-hub-Backend