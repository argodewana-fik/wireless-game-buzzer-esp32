# Wireless Game Buzzer ESP32

Sistem buzzer kuis nirkabel yang dibangun di platform ESP32, memanfaatkan protokol ESP-NOW yang sangat cepat untuk komunikasi yang andal dengan latensi rendah. Proyek ini menampilkan antarmuka juri berbasis web, memastikan penilaian yang adil dan akurat untuk acara kuis atau kompetisi trivia.

## 🌟 Fitur

- **Respons Sangat Cepat**: Memanfaatkan protokol ESP-NOW untuk komunikasi dengan latensi minimal
- **Operasi Nirkabel**: Tidak perlu kabel rumit antara buzzer dan unit kontrol
- **Antarmuka Berbasis Web**: Juri/pembawa acara dapat mengontrol permainan melalui browser web
- **Sistem Penilaian yang Adil**: Deteksi akurat buzzer mana yang ditekan pertama kali
- **Dukungan Multi Buzzer**: Dapat menangani banyak pemain secara bersamaan
- **Konsumsi Daya Rendah**: Penggunaan daya yang efisien untuk sesi permainan yang panjang
- **Mudah Dibuat**: Menggunakan modul ESP32 yang mudah didapat

## 🔧 Kebutuhan Perangkat Keras

- **Kontroler Utama**: 1x Board Pengembangan ESP32
- **Buzzer**: Beberapa board ESP32 (satu per pemain/tim)
- **Sumber Daya**: Adaptor daya USB atau power bank untuk setiap ESP32
- **Tombol**: Tombol tekan untuk setiap unit buzzer
- **Opsional**: LED untuk umpan balik visual, buzzer untuk umpan balik audio

## 📋 Kebutuhan Perangkat Lunak

- Arduino IDE atau PlatformIO
- Paket Dukungan Board ESP32
- Library ESP-NOW (sudah termasuk dalam ESP32 core)
- Browser web untuk antarmuka juri

## 🚀 Instalasi

### 1. Menyiapkan Lingkungan Pengembangan

1. Install [Arduino IDE](https://www.arduino.cc/en/software) atau [PlatformIO](https://platformio.org/)
2. Tambahkan dukungan board ESP32:
   - Untuk Arduino IDE: Buka `File > Preferences` dan tambahkan URL ini ke "Additional Board Manager URLs":
     ```
     https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
     ```
   - Install "ESP32" dari Board Manager

### 2. Mengkloning Repository

```bash
git clone https://github.com/argodewana-fik/wireless-game-buzzer-esp32.git
cd wireless-game-buzzer-esp32
```

### 3. Mengunggah Kode

1. Buka proyek di IDE Anda
2. Konfigurasikan kode untuk pengaturan spesifik Anda (jumlah buzzer, pin GPIO, dll.)
3. Upload kode kontroler utama ke ESP32 juri
4. Upload kode buzzer ke ESP32 setiap pemain

## 💡 Penggunaan

### Operasi Dasar

1. **Nyalakan**: Nyalakan semua unit buzzer dan kontroler utama
2. **Koneksi**: Buzzer akan otomatis terpasang dengan kontroler melalui ESP-NOW
3. **Mulai Game**: Akses antarmuka web melalui alamat IP kontroler
4. **Bermain**: Pemain menekan buzzer mereka untuk menjawab pertanyaan
5. **Penilaian**: Juri dapat melihat pemain mana yang menekan buzzer pertama kali di antarmuka web

### Antarmuka Web

Antarmuka web menyediakan:
- Status buzzer secara real-time
- Identifikasi pemain
- Fungsi reset
- Pelacakan skor
- Opsi kontrol permainan

## 🔌 Diagram Pengkabelan

### Kontroler Utama
```
ESP32 Controller
├── GPIO XX - LED Status
├── GPIO XX - Tombol Reset
└── WiFi/ESP-NOW - Komunikasi
```

### Unit Buzzer
```
ESP32 Buzzer
├── GPIO XX - Tombol Buzzer (INPUT_PULLUP)
├── GPIO XX - LED Status
└── ESP-NOW - Komunikasi
```

## 🛠️ Konfigurasi

Edit bagian konfigurasi dalam kode untuk menyesuaikan:

```cpp
// Jumlah pemain
#define NUM_PLAYERS 4

// Pin GPIO
#define BUTTON_PIN 12
#define LED_PIN 2

// Konfigurasi ESP-NOW
// Tambahkan alamat MAC unit buzzer
```

## 📡 Protokol ESP-NOW

ESP-NOW adalah protokol komunikasi tanpa koneksi yang dikembangkan oleh Espressif. Fitur-fiturnya:
- Komunikasi cepat (latensi < 10ms)
- Tidak memerlukan router WiFi
- Konsumsi daya rendah
- Mendukung hingga 20 perangkat terpasang

## 🤝 Kontribusi

Kontribusi sangat diterima! Silakan kirimkan Pull Request. Untuk perubahan besar:

1. Fork repository
2. Buat branch fitur Anda (`git checkout -b feature/FiturMenakjubkan`)
3. Commit perubahan Anda (`git commit -m 'Menambahkan FiturMenakjubkan'`)
4. Push ke branch (`git push origin feature/FiturMenakjubkan`)
5. Buka Pull Request

## 📝 Lisensi

Proyek ini adalah open source dan tersedia di bawah [Lisensi MIT](LICENSE).

## 👨‍💻 Penulis

**Argo Dewana**
- Email: argodewana@fasilkom.narotama.ac.id
- GitHub: [@argodewana-fik](https://github.com/argodewana-fik)

## 🙏 Penghargaan

- Espressif Systems untuk platform ESP32 dan protokol ESP-NOW
- Komunitas Arduino dan PlatformIO
- Semua kontributor proyek ini

## 📞 Dukungan

Jika Anda mengalami masalah atau memiliki pertanyaan:
- Buka issue di GitHub
- Hubungi penulis melalui email
- Periksa dokumentasi dan issue yang ada terlebih dahulu

## 🔮 Pengembangan Masa Depan

- [ ] Menambahkan efek suara untuk aktivasi buzzer
- [ ] Mengimplementasikan mode tim
- [ ] Menambahkan beberapa mode permainan (first-to-answer, fastest-time, dll.)
- [ ] Membuat antarmuka aplikasi mobile
- [ ] Menambahkan indikator level baterai
- [ ] Mengimplementasikan riwayat dan statistik skor
- [ ] Menambahkan tema yang dapat dikonfigurasi untuk antarmuka web

---

**Selamat Bermain! 🎮🎯**
