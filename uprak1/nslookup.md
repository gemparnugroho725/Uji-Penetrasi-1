Berikut **daftar command penting nslookup** yang biasa digunakan oleh pentester saat melakukan *reconnaissance / footprinting*. Semua contoh bisa langsung dipakai di Windows, Linux, atau Kali.

---

# ✅ **DAFTAR COMMAND PENTESTER UNTUK `nslookup`**

## 1️⃣ **Query Alamat IP dari Sebuah Domain**

```bash
nslookup example.com
```

**Fungsi:** Mengetahui IP Address utama dari domain.

---

## 2️⃣ **Reverse DNS Lookup (IP → Domain)**

```bash
nslookup 8.8.8.8
```

**Fungsi:** Mengetahui domain apa yang menggunakan IP tersebut.

---

## 3️⃣ **Mencari Semua Record DNS (ANY Query)**

```bash
nslookup -type=any example.com
```

**Fungsi:** Mengambil semua informasi DNS yang tersedia.

---

## 4️⃣ **Melihat Record MX (Mail Server)**

```bash
nslookup -type=mx example.com
```

**Fungsi:** Mengetahui server email perusahaan (penting untuk social engineering & phishing test).

---

## 5️⃣ **Melihat Record NS (Nameserver)**

```bash
nslookup -type=ns example.com
```

**Fungsi:** Mengetahui DNS server mana yang dipakai target.

---

## 6️⃣ **Melihat Record TXT**

```bash
nslookup -type=txt example.com
```

**Fungsi:** Menemukan SPF, DMARC, DKIM → bisa dipakai untuk analisis email security.

---

## 7️⃣ **Melihat Record CNAME**

```bash
nslookup -type=cname www.example.com
```

**Fungsi:** Melihat alias domain, biasanya mengarah ke layanan lain (Cloudflare, AWS, dll).

---

## 8️⃣ **Query ke DNS Server Tertentu (Custom DNS)**

```bash
nslookup example.com 1.1.1.1
```

**Fungsi:** Mengambil data DNS langsung dari server tertentu (Cloudflare, Google DNS, DNS milik target, dll).

---

## 9️⃣ **Masuk ke Mode Interaktif**

```bash
nslookup
```

Kemudian bisa jalankan:

### 🔹 Set tipe query

```bash
set type=mx
```

### 🔹 Query domain

```bash
example.com
```

### 🔹 Set DNS server manual

```bash
server 8.8.8.8
```

### 🔹 Keluar

```bash
exit
```

---

## 🔟 **Melakukan Zone Transfer (jika server rentan)**

> ⚠️ *Hanya untuk lab / izin resmi. Banyak server modern sudah menolak AXFR.*

```bash
nslookup
set type=any
ls -d example.com
```

Jika berhasil → akan menampilkan seluruh data zona DNS perusahaan (subdomain lengkap, mail server, host internal).

---

# 📌 **BONUS – Contoh Workflow Pentester dengan nslookup**

1. Cari IP utama

   ```bash
   nslookup target.com
   ```
2. Cari NS

   ```bash
   nslookup -type=ns target.com
   ```
3. Test zone transfer ke nameserver

   ```bash
   nslookup
   server ns1.target.com
   ls -d target.com
   ```
4. Ambil MX & TXT untuk analisis email

   ```bash
   nslookup -type=mx target.com
   nslookup -type=txt target.com
   ```

---

Kalau mau saya lanjutkan tools footprinting lainnya seperti **theHarvester, maltego, HTTrack, recon-ng**, saya bisa buatkan **daftar command lengkap + rangkuman** seperti ini.
