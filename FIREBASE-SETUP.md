# Sediakan perkongsian keluarga (Firebase)

Aplikasi berfungsi tanpa ini (data dalam telefon sahaja). Ikut langkah di bawah
hanya jika mahu ahli keluarga nampak dan tambah catatan yang sama. Percuma, sekitar 10 minit.

## 1. Buat projek Firebase
1. Buka https://console.firebase.google.com dan log masuk dengan akaun Google.
2. **Add project** → beri nama (cth. `diari-keluarga`) → matikan Google Analytics → **Create project**.

## 2. Hidupkan pangkalan data
1. Menu kiri: **Build → Firestore Database → Create database**.
2. Lokasi: pilih `asia-southeast1 (Singapore)`.
3. Pilih **Start in production mode** → **Create**.
4. Tab **Rules** → padam semua teks → tampal kandungan fail `firestore.rules` dalam repo ini → **Publish**.

## 3. Daftar app web dan salin konfigurasi
1. Halaman utama projek → ikon **</>** (Web) → beri nama → **Register app** (tidak perlu Firebase Hosting).
2. Salin blok `firebaseConfig` yang dipaparkan (apiKey, authDomain, projectId, ...).

## 4. Tampal konfigurasi ke dalam `config.js`
Dalam repo GitHub, buka `config.js` → ikon pensel (Edit) → gantikan kandungan dengan:

```js
window.DIARI_FIREBASE = {
  apiKey: "...",
  authDomain: "...",
  projectId: "...",
  storageBucket: "...",
  messagingSenderId: "...",
  appId: "..."
};
```

Commit. Tunggu 1–2 minit untuk Pages kemas kini.

> Nilai `apiKey` ini bukan rahsia. Ia hanya mengenal pasti projek anda. Keselamatan data datang daripada peraturan (rules) dan pautan rahsia.

## 5. Guna
1. Di telefon Mak: tab **Lagi → Kongsi dengan keluarga → Aktifkan**.
2. Tekan **Hantar pautan melalui WhatsApp** kepada ahli keluarga.
3. Ahli keluarga buka pautan → **OK** untuk sertai. Selepas itu semua telefon segerak automatik.

## Cara keselamatan berfungsi
- Setiap diari ada ID rahsia 26 aksara dalam pautan (seperti "sesiapa yang ada pautan" pada Google Docs).
- Peraturan Firestore tidak membenarkan senarai semua diari. Tanpa ID, tiada siapa boleh baca.
- **Sesiapa yang ada pautan boleh melihat dan mengubah.** Hantar hanya kepada keluarga. Jika pautan bocor, tekan **Padam data dari awan**, kemudian **Aktifkan** semula untuk pautan baharu.
