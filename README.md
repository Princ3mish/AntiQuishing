# 👁️‍🗨️ CipherSight: Anti-Quishing Security

![Python](https://img.shields.io/badge/python-3.10%2B-blue.svg)
![Docker](https://img.shields.io/badge/docker-supported-blue.svg)
![Hardware](https://img.shields.io/badge/hardware-ESP32-green.svg)
![License](https://img.shields.io/badge/license-MIT-purple.svg)

**CipherSight** is a hybrid hardware-software Point of Sale (POS) security solution designed to prevent QR Phishing ("Quishing") attacks. 

By leveraging **(2,2) Visual Cryptography**, the system splits sensitive transaction data into two unreadable shares: one displayed on the customer's mobile device, and the other transmitted securely via MQTT to a dedicated hardware terminal (ESP32). The data can only be resolved when both the physical hardware and the user's session are physically synced.

---

## ✨ Key Features
* **Visual Cryptography Engine:** Dynamically shreds transaction QR codes into cryptographic noise patterns.
* **Hardware-Secured Display:** ESP32 integration with an SSD1306 OLED to display real-time physical shares via MQTT.
* **Two-Factor Visual Verification:** Requires physical proximity and a hardware sync code to reconstruct the payment link.
* **AR Simulation:** Includes an OpenCV/Aruco-based Augmented Reality scanner to simulate physical scanning of the shares.
* **Containerized & Portable:** Fully dockarized backend with an automated Windows setup script.

---

## 📁 Repository Structure

* **`core/`**: The Visual Cryptography engine (`shredder.py`) and orchestrator.
* **`pos/`**: The Flask-based POS web application (Merchant Dashboard & Customer Portal).
* **`firmware/`**: C++ source code (`esp32_mqtt.ino`) for the ESP32 microcontroller.
* **`simulation/`**: AR scanner (`ar_overlay.py`) using OpenCV.
* **`webapp/`**: Alternative web-based hardware verification frontend.

---

## 🚀 Getting Started

### Prerequisites
* Python 3.9+
* ESP32 Microcontroller with an SSD1306 OLED display
* Docker & Docker Compose (Optional, for containerized deployment)

### Option 1: Automated Local Setup (Windows)
For a quick, one-click setup on Windows machines:
1. Double-click the `start.bat` file.
2. The script will automatically create a Python virtual environment, install all dependencies, start the Flask server, and launch the Merchant POS System in your default browser.

### Option 2: Manual Local Setup (Mac/Linux/Windows)
1. Clone the repository and navigate to the root directory.
2. Create a virtual environment and activate it:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
