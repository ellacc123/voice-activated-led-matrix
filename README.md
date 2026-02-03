---

## 📺 Demo

<p align="center">
  <a href="https://www.youtube.com/shorts/5sUCpxtb52w">
    <img src="assets/demo-thumbnail.png" alt="Demo video" width="300"/>
  </a>
</p>

Speak "Red", "Green", or "Blue" → the corresponding LEDs light up in real-time.

---

## 💡 Overview

A voice-controlled 5x5 LED matrix that responds to spoken color commands, built as part of UW's EE 399 Singapore Study Abroad program. The system runs a TinyML model directly on the microcontroller for real-time speech recognition—no cloud required.

Inspired by immersive public displays at Gardens by the Bay and the National Museum of Singapore.

---

## 🏗 System Architecture

```
┌──────────┐    ┌─────────────┐    ┌─────────────┐    ┌────────────┐
│  Button  │───▶│ Microphone  │───▶│  Edge       │───▶│  5x5 LED   │
│  Press   │    │ (MP34DT05)  │    │  Impulse ML │    │  Matrix    │
└──────────┘    └─────────────┘    └─────────────┘    └────────────┘
                                          │
                                   ≥60% confidence
                                   triggers output
```

| Component | Description |
|-----------|-------------|
| **Input** | Button activates microphone for voice capture |
| **Processing** | Edge Impulse ML model classifies speech (Blue / Red / Green / None) |
| **Output** | 5x5 LED matrix displays corresponding color pattern |

---

## ⚡ Technical Highlights

**Embedded ML**
- Deployed TinyML model on Arduino Nano 33 BLE Sense
- **95.6% classification accuracy** on voice commands
- 60% confidence threshold tuned through empirical testing
- Real-time inference with no cloud dependency

**Hardware Optimization**
- Reduced pin usage from 25 → 3 by grouping same-color LEDs
- Eliminated need for second microcontroller
- Clean circuit design on breadboard prototype

**Evaluation**
- Tested across quiet (hallway) and noisy (classroom) environments
- Achieved 90% accuracy in quiet conditions, 60% in noisy
- Identified "Red" as lowest-accuracy command via confusion matrix analysis

---

## 🛠 Tech Stack

| Category | Technologies |
|----------|-------------|
| **Hardware** | Arduino Nano 33 BLE Sense, MP34DT05 MEMS microphone, 5x5 LED matrix |
| **ML Platform** | Edge Impulse (data collection, training, deployment) |
| **Firmware** | C++ (modified `nano_ble33_sense_microphone` example) |
| **Dataset** | 4-class audio classification (Blue, Green, Red, None) |

---

## 📊 Results

| Environment | Blue | Green | Red |
|-------------|------|-------|-----|
| Quiet (hallway) | 9/10 | 8/10 | 6/10 |
| Noisy (classroom) | 6/10 | 6/10 | 4/10 |

**Key findings:**
- Background noise significantly impacts recognition accuracy
- "Red" consistently underperforms (aligned with confusion matrix predictions)
- Proposed fix: directional microphone cone to isolate voice input

---

## 🚀 Getting Started

### Hardware Required
- Arduino Nano 33 BLE Sense
- 15 LEDs (5 red, 5 green, 5 blue)
- Resistors, breadboard, jumper wires
- Push button

### Software Setup

1. Clone this repository
   ```bash
   git clone https://github.com/your-username/sound-activated-light-show.git
   ```

2. Import the Edge Impulse model
   - Open [Edge Impulse Studio](https://studio.edgeimpulse.com/)
   - Deploy to Arduino library

3. Flash the Arduino
   ```bash
   # Open in Arduino IDE and upload to board
   ```

---

## 🔮 Future Improvements

- **LED Matrix Panels** — Replace individual LEDs for complex art patterns
- **Directional Microphone** — Add cone housing to reduce ambient noise
- **Accent Diversity** — Expand training dataset for multilingual support
- **Adjustable Height** — Make microphone accessible to all users

---

## 👥 Team

Built for **EE 399 — Singapore Study Abroad Program** at the University of Washington

**Ella Cao** · **Eileen Nguyen**

---

## 📚 References

- [Edge Impulse + Arduino Tutorial](https://docs.arduino.cc/tutorials/nano-33-ble-sense/edge-impulse/)
- [CloudColourSounds Dataset](https://mltools.arduino.cc/public/215176/latest)
- [Smart Cities & Digital Trust (IEEE)](https://doi.org/10.1109/scfc62024.2024.10698207)

---

<p align="center">
  <sub>Built in Singapore 🇸🇬 · September 2025</sub>
</p>
