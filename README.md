# FixSight (FixSight AR) 👁️🔧

> **An intelligent, multimodal AI troubleshooter and offline clinical decision support system for frontline workers and technicians.**

FixSight is an Android application designed to bridge the knowledge gap in offline and high-stakes environments. By combining on-device vision models with a local Retrieval-Augmented Generation (RAG) knowledge base, FixSight provides immediate, context-aware troubleshooting assistance and clinical decision guidelines—even without an active internet connection.

Whether assisting an Auxiliary Nurse Midwife (ANM) with diagnostic workflows in a rural clinic or guiding a technician through hardware repairs, FixSight acts as an expert companion that sees what you see and knows the official protocols.

---

## ✨ Key Features

*   **Multimodal AI Troubleshooting:** Utilize the device's camera to analyze physical environments, hardware, or symptoms. The vision model understands context and provides actionable steps based on visual input.
*   **Offline RAG Knowledge Base:** Powered by a local SQLite Full-Text Search (FTS) database compiled from official manuals (e.g., MoHFW and NHM guidelines).
*   **On-Device Inference:** Designed to run robust local LLM inferences on edge hardware (optimized for Snapdragon processors), ensuring privacy, low latency, and true offline capability.
*   **AR-Enhanced Guidance (Optional):** Contextual overlays to help identify specific components, dials, or diagnostic indicators during the troubleshooting process.
*   **Domain-Agnostic Architecture:** While initially loaded with clinical guidelines for ANMs, the backend can ingest technical manuals, repair guides, or IT infrastructure documentation.

## 🏗️ Architecture & Tech Stack

*   **Platform:** Android (Native Kotlin)
*   **On-Device AI Engine:** Google AI Edge LiteRT-LM SDK / OpenCL GPU Backends (`Backend.GPU()`)
*   **Knowledge Base (RAG):** Offline SQLite Full-Text Search (FTS) / Vector Database
*   **Multimodal/Vision:** Gemini models (via API for cloud escalation) and quantized local vision models.
*   **Core Tools:** Android Studio, Gradle, JNI.

## 🎯 Primary Use Cases

1.  **Clinical Decision Support (Healthcare):**
    Empowering ANMs and frontline health workers in rural areas with immediate access to official health protocols, diagnostic flowcharts, and visual symptom analysis without relying on network connectivity.
2.  **Hardware & Technical Troubleshooting:**
    Assisting field engineers in diagnosing equipment failures by pointing the camera at a machine, retrieving the relevant service manual from the local RAG database, and providing step-by-step repair instructions.

## 🚀 Getting Started

### Prerequisites

*   Android Studio (Latest stable version)
*   Android device running Android 12.0+ (Snapdragon 8 Gen series or equivalent recommended for optimal local LLM inference).
*   *Note: Due to memory requirements for local LLMs, a device with at least 8GB+ RAM is strongly recommended.*

### Installation & Setup

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/yourusername/FixSight.git](https://github.com/yourusername/FixSight.git)
    cd FixSight
    ```
2.  **Download the Quantized Models:**
    *   Due to GitHub file size limits, the pre-quantized `.litertlm` models are not included in the repository.
    *   Download the required models from [Insert Link/Instructions Here] and place them in the `app/src/main/assets/models/` directory.
3.  **Initialize the Knowledge Base:**
    *   Ensure the SQLite RAG database (`knowledge_base.db`) is located in the `app/src/main/assets/db/` directory.
4.  **Build the Project:**
    *   Open the project in Android Studio.
    *   Sync Gradle files.
    *   Build and run the application on your physical Android device (Emulators are not recommended for local GPU AI inference).

## 🧠 How the RAG Pipeline Works

1.  **Query Input:** The user inputs a query via text or captures an image of the problem.
2.  **Retrieval:** The application queries the local SQLite FTS database against the pre-loaded official manuals.
3.  **Augmentation:** The retrieved context (and image data, if applicable) is passed to the local LLM.
4.  **Generation:** The model synthesizes the official guidelines with the visual context to provide a precise, grounded troubleshooting step.

## 🤝 Contributing

Contributions are welcome! If you'd like to improve the RAG pipeline, optimize the JNI bindings, or expand the UI, please open an issue or submit a pull request.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request



## 🏆 Acknowledgements

*   Data sources utilized for the ANM knowledge base include official guidelines from the Ministry of Health and Family Welfare (MoHFW).
