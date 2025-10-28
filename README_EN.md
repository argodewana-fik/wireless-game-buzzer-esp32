# Wireless Game Buzzer ESP32

A wireless quiz buzzer system built on the ESP32 platform, utilizing the ultra-fast ESP-NOW protocol for reliable, low-latency communication. This project features a web-based judge interface, ensuring fair and accurate scoring for any game show or trivia competition.

## 🌟 Features

- **Ultra-Fast Response**: Utilizes ESP-NOW protocol for minimal latency communication
- **Wireless Operation**: No need for complex wiring between buzzers and control unit
- **Web-Based Interface**: Judge/host can control the game through a web browser
- **Fair Scoring System**: Accurate detection of which buzzer was pressed first
- **Multiple Buzzers Support**: Can handle multiple players simultaneously
- **Low Power Consumption**: Efficient power usage for long gaming sessions
- **Easy to Build**: Uses readily available ESP32 modules

## 🔧 Hardware Requirements

- **Main Controller**: 1x ESP32 Development Board
- **Buzzers**: Multiple ESP32 boards (one per player/team)
- **Power Supply**: USB power adapters or battery packs for each ESP32
- **Buttons**: Push buttons for each buzzer unit
- **Optional**: LEDs for visual feedback, buzzers for audio feedback

## 📋 Software Requirements

- Arduino IDE or PlatformIO
- ESP32 Board Support Package
- ESP-NOW library (included in ESP32 core)
- Web browser for the judge interface

## 🚀 Installation

### 1. Setting Up the Development Environment

1. Install [Arduino IDE](https://www.arduino.cc/en/software) or [PlatformIO](https://platformio.org/)
2. Add ESP32 board support:
   - For Arduino IDE: Go to `File > Preferences` and add this URL to "Additional Board Manager URLs":
     ```
     https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
     ```
   - Install "ESP32" from the Board Manager

### 2. Cloning the Repository

```bash
git clone https://github.com/argodewana-fik/wireless-game-buzzer-esp32.git
cd wireless-game-buzzer-esp32
```

### 3. Uploading the Code

1. Open the project in your IDE
2. Configure the code for your specific setup (number of buzzers, GPIO pins, etc.)
3. Upload the main controller code to the judge's ESP32
4. Upload the buzzer code to each player's ESP32

## 💡 Usage

### Basic Operation

1. **Power On**: Turn on all buzzer units and the main controller
2. **Connection**: The buzzers will automatically pair with the controller via ESP-NOW
3. **Start Game**: Access the web interface through the controller's IP address
4. **Play**: Players press their buzzers to answer questions
5. **Judging**: The judge can see which player buzzed first on the web interface

### Web Interface

The web interface provides:
- Real-time buzzer status
- Player identification
- Reset functionality
- Score tracking
- Game control options

## 🔌 Wiring Diagram

### Main Controller
```
ESP32 Controller
├── GPIO XX - Status LED
├── GPIO XX - Reset Button
└── WiFi/ESP-NOW - Communication
```

### Buzzer Units
```
ESP32 Buzzer
├── GPIO XX - Buzzer Button (INPUT_PULLUP)
├── GPIO XX - Status LED
└── ESP-NOW - Communication
```

## 🛠️ Configuration

Edit the configuration section in the code to customize:

```cpp
// Number of players
#define NUM_PLAYERS 4

// GPIO Pins
#define BUTTON_PIN 12
#define LED_PIN 2

// ESP-NOW Configuration
// Add MAC addresses of buzzer units
```

## 📡 ESP-NOW Protocol

ESP-NOW is a connectionless communication protocol developed by Espressif. It features:
- Fast communication (< 10ms latency)
- No WiFi router required
- Low power consumption
- Supports up to 20 paired devices

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 👨‍💻 Author

**Argo Dewana**
- Email: argodewana@fasilkom.narotama.ac.id
- GitHub: [@argodewana-fik](https://github.com/argodewana-fik)

## 🙏 Acknowledgments

- Espressif Systems for the ESP32 platform and ESP-NOW protocol
- The Arduino and PlatformIO communities
- All contributors to this project

## 📞 Support

If you encounter any issues or have questions:
- Open an issue on GitHub
- Contact the author via email
- Check the documentation and existing issues first

## 🔮 Future Enhancements

- [ ] Add sound effects for buzzer activation
- [ ] Implement team mode
- [ ] Add multiple game modes (first-to-answer, fastest-time, etc.)
- [ ] Create mobile app interface
- [ ] Add battery level indicators
- [ ] Implement scoring history and statistics
- [ ] Add configurable themes for the web interface

---

**Happy Buzzing! 🎮🎯**
