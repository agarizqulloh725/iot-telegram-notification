Untuk membuat bot Telegram yang menggunakan webhook untuk pembaruan dan mengimplementasikan kode ESP8266 yang diberikan, ikuti langkah-langkah berikut:

### Langkah 1: Menyiapkan ESP8266
1. **Instal Arduino IDE**: Unduh dan instal Arduino IDE dari [situs web resmi Arduino](https://www.arduino.cc/en/software).
2. **Instal Board ESP8266 di Arduino IDE**:
   - Buka Arduino IDE, pergi ke File > Preferences.
   - Di bidang "Additional Board Manager URLs", tambahkan `http://arduino.esp8266.com/stable/package_esp8266com_index.json` dan klik "OK".
   - Pergi ke Tools > Board > Boards Manager, cari "ESP8266", dan instal.
3. **Instal Libraries**:
   - Pergi ke Sketch > Include Library > Manage Libraries.
   - Cari dan instal "UniversalTelegramBot" dan "ArduinoJson".
4. **Sambungkan ESP8266 Anda**:
   - Sambungkan modul ESP8266 ke komputer Anda melalui kabel USB.
   - Pilih board yang benar dari Tools > Board dan pilih port dari Tools > Port.

### Langkah 2: Membuat Bot Telegram
1. **Bicara dengan BotFather**:
   - Buka Telegram dan cari "BotFather".
   - Mulai percakapan dan buat bot baru dengan mengirim perintah `/newbot`.
   - Ikuti instruksi untuk menentukan nama dan username untuk bot Anda.
   - BotFather akan memberikan token untuk bot Anda; simpan token ini dengan aman.

### Langkah 3: Memprogram ESP8266 Anda
1. **Perbarui Sketsa**:
   - Ganti `ssid`, `password`, dan `botToken` dalam sketsa yang disediakan dengan kredensial WiFi Anda dan token bot Telegram dari BotFather.
   - Sesuaikan parameter lain sesuai kebutuhan, seperti array `chat_ids` untuk memasukkan ID pengguna Telegram Anda (dapatkan ini dengan memulai obrolan dengan "userinfobot" di Telegram).
2. **Unggah Kode**:
   - Kompilasi dan unggah sketsa ke ESP8266 Anda menggunakan Arduino IDE.

### Langkah 4: Menyiapkan Webhook Telegram
1. **Gunakan Server HTTPS**: Telegram memerlukan HTTPS untuk webhook. Anda akan memerlukan server dengan HTTPS yang diaktifkan untuk menangani permintaan.
2. **Atur Webhook**:
   - Gunakan panggilan API berikut untuk mengatur URL webhook Anda (ganti `<your_bot_token>` dan `<your_https_url>` dengan token bot dan URL server aktual Anda):
     ```
     https://api.telegram.org/bot<your_bot_token>/setWebhook?url=<your_https_url>
     ```
   - Anda dapat menggunakan alat seperti Postman atau curl untuk membuat panggilan API ini.

### Langkah 5: Mengimplementasikan Logika Server
1. **Endpoint Server**:
   - Tulis kode sisi server untuk menangani permintaan webhook masuk dari Telegram.
   - Analisis pesan atau perintah dan kirim respons kembali ke pengguna.
2. **Komunikasi dengan ESP8266**:
   - Server Anda harus berkomunikasi dengan ESP8266, mungkin melalui MQTT atau permintaan HTTP langsung, untuk memicu aksi berdasarkan perintah Telegram.

### Langkah 6: Pengujian
1. **Berinteraksi dengan Bot Anda**:
   - Kirim pesan ke bot Telegram Anda untuk melihat apakah ia merespons seperti yang diharapkan.
   - Pantau keluaran serial dari ESP8266 untuk memastikan ia memproses dan merespons sinyal dengan tepat.

Proses ini mengintegrasikan interaksi bot Telegram melalui webhook dan kontrol perangkat keras ESP8266, memungkinkan Anda untuk memantau dan mengontrol perangkat secara remote melalui Telegram.
