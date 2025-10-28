# 🔔 Real-Time Wireless Quiz Buzzer (ESP-NOW)

A wireless quiz buzzer system built on the ESP32 platform, utilizing the ultra-fast ESP-NOW protocol for reliable, low-latency communication.  
This project features a real-time, web-based judge interface powered by WebSockets, ensuring fair, millisecond-accurate scoring for any game show or trivia competition.

This project is designed to solve the problem of subjectivity and human error in determining who pressed the button first, with millisecond-level precision.

---

## ✨ Key Features

| Feature                     | Description |
|----------------------------|-------------|
| Ultra-Low Latency          | Uses ESP-NOW for instant communication (<10ms) without WiFi connection delays or TCP/IP handshakes. |
| Real-Time Judge Interface  | The judge's control panel gets updates in real time using WebSockets. No page refresh needed. |
| Universal Access           | Judge can use any browser on any device (phone, laptop) connected to the Host's WiFi AP. |
| High Accuracy              | System objectively determines one winner with millisecond precision, eliminating debates. |
| Low Cost                   | Built using affordable and widely available components. |
| Simple Setup               | No external router required — the Host acts as an AP ("Smart Bell"). |

---

## 💡 Concept & How It Works

The core idea is to separate the "Button" (Sender) from the "Brain" (Host).

### 1. Button Unit (Sender) — The "Dumb" Device
| Property         | Value                                                                 |
|------------------|-----------------------------------------------------------------------|
| Hardware         | ESP32-C3 SuperMini                                                    |
| Responsibility   | When the physical button is pressed, immediately send a packet via ESP-NOW (e.g. ID `'A'`). |
| WiFi Connection  | None. The Sender does **not** join any WiFi network.                 |
| Knowledge of Game State | None. It doesn't know who already won.                       |
| Why It's Fast    | No TCP/IP, no HTTP, just raw ESP-NOW broadcast to Host MAC.           |

### 2. Central Unit (Host) — The "Smart" Device
| Property           | Value                                                                                  |
|--------------------|----------------------------------------------------------------------------------------|
| Hardware           | ESP32-WROOM32                                                                          |
| Responsibility #1  | Listen for ESP-NOW packets from all Senders.                                           |
| Responsibility #2  | Decide the winner (first press wins), then lock the round to ignore late presses.     |
| Responsibility #3  | Act as WiFi AP (`"Smart Bell"`) and serve a web dashboard + WebSocket for the judge.  |

---

## 🔧 System Architecture

The project uses a **Star Network Topology**:

- The Host (ESP32-WROOM32) acts as the center.
- All Sender units (ESP32-C3) transmit directly to the Host using ESP-NOW.
- The Judge connects to the Host's Access Point over WiFi and controls the round.

```mermaid
graph TD
    subgraph "Sender Units (Teams)"
        direction TB
        S_A(Physical Button A) --> C3_A[ESP32-C3 'A']
        S_B(Physical Button B) --> C3_B[ESP32-C3 'B']
        S_C(Physical Button C) --> C3_C[ESP32-C3 'C']
    end

    subgraph "Central Unit (Host / Judge)"
        direction LR
        Host[ESP32-WROOM32 Host]
        Judge(Judge's Device: Phone/Laptop)

        Host -- "1. Creates Network" --> AP((WiFi AP 'Smart Bell'))
        Judge -- "2. Connects to WiFi" --> AP
        Host -- "4. Real-time UI Update" --> Judge
        Judge -- "3. Open IP & Send Commands" --> Host
    end

    C3_A -- "ESP-NOW Data (ID: 'A')" --> Host
    C3_B -- "ESP-NOW Data (ID: 'B')" --> Host
    C3_C -- "ESP-NOW Data (ID: 'C')" --> Host
