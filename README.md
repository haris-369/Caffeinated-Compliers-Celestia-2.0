<div align="center">

# ☕ Caffeinated Compilers | Celestia 2.0
## GHS: Golden Hour System

### A compact IoT emergency communication device that connects a person in distress to an AI assistant and, when available, a remote doctor, with live voice, video and location.

![Hackathon](https://img.shields.io/badge/Hackathon-Celestia_2.0-blueviolet)
![Status](https://img.shields.io/badge/Status-Prototype-orange)

</div>

---

## 🚀 The Problem
The first hour after a medical emergency, the "golden hour", is when timely action matters most[cite: 3]. But the person in distress is often alone or surrounded by untrained bystanders, and no doctor can see or hear what is happening[cite: 3]. Responders arrive without a clear picture of the patient's condition or exact location, while the patient waits without guidance[cite: 3]. Meanwhile, many IoT health devices stop at measuring vitals—they generate data, but they do not connect the person to anyone who can act on it[cite: 3].

## 💡 Our Solution
GHS bridges the communication gap during the golden hour[cite: 3]. It is a compact IoT device that connects a person in distress with an AI assistant and, when available, a doctor, with live location, voice and video[cite: 3].

### Key Features
* **Emergency Triggered:** GHS activates and sends its GPS location to the backend[cite: 3].
* **AI First Response:** Voice AI gives safety-oriented, non-diagnostic first-response guidance (`Mic → Speech-to-Text → AI → Text-to-Speech → Speaker`)[cite: 2, 3].
* **Doctor Joins:** Camera, display, mic and speaker become a two-way telemedicine link to a browser dashboard using WebRTC[cite: 2, 3].
* **GPS Coordination:** Live GPS powers navigation, hospital search and ambulance coordination[cite: 3].

## ⚙️ Architecture
The physical device stays small; the AI, hospital search, emergency coordination, navigation, summarization, and communication logic happen in the cloud/backend[cite: 5].

```mermaid
flowchart LR
    subgraph D["GHS Device"]
        H["Camera · Display · Mic · Speaker · GPS"] --> C[Controller]
    end
    C -- "Wi-Fi / 4G" --> B
    subgraph B["GHS Backend"]
        E[Emergency Manager] --- L[Location Service]
        E --- DC[Doctor Connection]
        E --- A[AI Service]
        E --- DB[(PostgreSQL)]
    end
    B --> AI[AI Assistant]
    B --> DR[Doctor Dashboard]
    B --> ES[Emergency Services]
