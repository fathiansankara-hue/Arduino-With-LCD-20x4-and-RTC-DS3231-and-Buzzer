# Arduino Jam Digital dengan LCD 20x4, RTC DS3231, dan Buzzer

Proyek ini adalah sebuah jam digital sederhana berbasis Arduino Uno yang menampilkan waktu, tanggal, dan hari pada modul LCD 20x4 menggunakan modul RTC DS3231. Proyek ini juga menghasilkan bunyi singkat pada buzzer setiap siklus loop.

## Fitur

- Menampilkan hari dalam bahasa Indonesia
- Menampilkan tanggal dan waktu secara real-time dari RTC DS3231
- Tampilan LCD 20 kolom x 4 baris
- Nada buzzer singkat setiap loop program
- Reset waktu otomatis jika RTC kehilangan daya

## Komponen

- Arduino Uno
- Modul LCD 20x4 dengan antarmuka 6 pin digital
- Modul RTC DS3231
- Buzzer pasif / speaker kecil
- Kabel jumper
- Breadboard (opsional)

## Pin Koneksi (Referensi)

- LCD: `RS=7`, `EN=6`, `D4=5`, `D5=4`, `D6=3`, `D7=2`
- Buzzer: `D8`
- Pin tambahan: `D10` diatur sebagai OUTPUT tetapi tidak digunakan dalam logika saat ini
- RTC DS3231: biasanya `SDA=A4`, `SCL=A5`, VCC, GND

> Pastikan koneksi I2C RTC dan kabel power tersambung dengan benar.

## Library yang Digunakan

- `RTClib` oleh Adafruit
- `LiquidCrystal`

Dependencies sudah didefinisikan di `platformio.ini`.

## Cara Build dan Upload

1. Buka proyek di PlatformIO.
2. Pastikan board yang digunakan adalah `Arduino Uno`.
3. Jalankan build:

   ```bash
   pio run
   ```

4. Upload ke board:

   ```bash
   pio run --target upload
   ```

## Penjelasan Kode Utama

- `lcd.begin(20, 4)` menginisialisasi layar LCD.
- `rtc.begin()` memulai komunikasi dengan modul RTC.
- Jika RTC kehilangan daya (`rtc.lostPower()`), waktu akan disetel ke waktu kompilasi program.
- Fungsi `printAngka()` memastikan angka ditampilkan dengan format dua digit.
- `loop()` membaca waktu dari RTC dan menampilkan hari, tanggal, serta jam di LCD.
- `tone(8, 1000, 50)` memainkan bunyi singkat pada pin buzzer.

## Catatan

- Jika menggunakan modul LCD I2C, maka wiring dan library perlu disesuaikan.
- Pastikan baterai backup RTC terpasang agar modul mempertahankan waktu saat power off.
- Untuk penyesuaian lebih lanjut, tambahkan fitur alarm atau pengaturan manual waktu di dalam kode.

## Lisensi

Proyek ini dapat digunakan dan dimodifikasi untuk keperluan pembelajaran dan hobi.
