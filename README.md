# Blueprint
## **Mail Service PERUMDAMTS**:

### 🏁 Rekapitulasi Rencana Pengembangan

* [cite_start]**Prioritas Utama**: Pembangunan **Dashboard Admin Master Data** sebagai fondasi sistem sebelum masuk ke fitur persuratan Staff[cite: 1].
* [cite_start]**Teknologi Inti**: Next.js 16.2.2 dengan sistem `proxy.ts` di root untuk *external rewrite* dan injeksi JWT dinamis[cite: 1].
* [cite_start]**Keamanan & Akses**: Integrasi Appwrite REST API dengan sistem *caching* JWT untuk menghindari *rate limit* serta pembagian peran (Admin vs Staff) melalui `labels[]`[cite: 1].
* [cite_start]**Antarmuka Ganda (UI)**: Tersedia pilihan **Template Klasik** (Master-Detail) untuk familiaritas dan **Template Modern** (Gmail-style) untuk efisiensi, yang dapat diganti melalui pengaturan profil[cite: 1].
* [cite_start]**Fitur Ramah Pengguna**: *Auto-save* draf, tombol buang draf dengan konfirmasi, serta **Tour Guide** interaktif yang bisa dilewati (*skip*)[cite: 1].
* **Prinsip Desain (60:30:10)**:
    * [cite_start]**60% (Base)**: `bg-slate-50` (Area konten & tabel)[cite: 1].
    * [cite_start]**30% (Secondary)**: `bg-indigo-900` (Sidebar & navigasi)[cite: 1].
    * [cite_start]**10% (Accent)**: `bg-amber-500` (Tombol aksi utama & bantuan)[cite: 1].

---

### 📋 Checklist Persiapan untuk Tim Junior

1.  [cite_start]**Inisialisasi Project**: Setup Next.js, Tailwind, dan ShadcnUI[cite: 1].
2.  [cite_start]**Koneksi Infrastruktur**: Konfigurasi `proxy.ts` dan `appwrite-rest.ts` di folder `lib`[cite: 1].
3.  [cite_start]**Pengaturan Tema**: Memastikan variabel warna `60:30:10` terdaftar di Tailwind Config[cite: 1].
4.  [cite_start]**Implementasi Master Data**: Mulai dengan CRUD `mail-types` dan `mail-categories` sebagai latihan pertama menggunakan TanStack Table dan Zod[cite: 1].
5.  [cite_start]**Onboarding Logic**: Menyiapkan *Floating Help Button* dan logika *Tour Guide* pertama[cite: 1].