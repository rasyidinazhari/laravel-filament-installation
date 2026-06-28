# 🚀 Laravel Filament — Dashboard & CRUD Admin Panel

> **Modul Praktikum Laravel 13 — Pertemuan 15**
> Sistem Informasi Akademik (SIA)

[![Laravel](https://img.shields.io/badge/Laravel-13-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)](https://laravel.com)
[![Filament](https://img.shields.io/badge/Filament-4-FDAE4B?style=for-the-badge&logo=laravel&logoColor=white)](https://filamentphp.com)
[![PHP](https://img.shields.io/badge/PHP-8.3-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://php.net)
[![MySQL](https://img.shields.io/badge/MySQL-Latest-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://mysql.com)

---

## 📋 Daftar Isi

- [Tujuan Pembelajaran](#-tujuan-pembelajaran)
- [Prasyarat](#-prasyarat)
- [Spesifikasi Teknologi](#-spesifikasi-teknologi)
- [Studi Kasus](#-studi-kasus)
- [Alokasi Waktu](#-alokasi-waktu)
- [Apa itu Filament?](#-apa-itu-filament)
- [Instalasi Filament](#-instalasi-filament)
- [Menjalankan Aplikasi](#-menjalankan-aplikasi)
- [Membuat User Admin](#-membuat-user-admin-filament)
- [Membatasi Akses Admin](#-membatasi-akses-hanya-admin)
- [CRUD Mahasiswa](#-crud-mahasiswa)
- [CRUD Dosen](#-crud-dosen)
- [CRUD Mata Kuliah](#-crud-mata-kuliah)
- [Relasi Model](#-relasi-model)
- [CRUD Kelas Mata Kuliah](#-crud-kelas-mata-kuliah)
- [Navigation Icons](#-navigation-icons)
- [Hasil Dashboard](#-hasil-dashboard)
- [Pengujian](#-pengujian)
- [Slide Presentasi](#-slide-presentasi)
- [Troubleshooting](#-troubleshooting)
- [Referensi](#-referensi)

---

## 🎯 Tujuan Pembelajaran

Setelah mengikuti praktikum ini, mahasiswa mampu:

1. **Memahami konsep Admin Panel** pada Laravel
2. **Menginstal Laravel Filament** sebagai package admin panel
3. **Membuat akun administrator** Filament
4. **Membuat dashboard admin** dengan tampilan modern
5. **Membuat CRUD** Mahasiswa, Dosen, dan Mata Kuliah
6. **Membuat relasi** pada Kelas Mata Kuliah menggunakan Eloquent Relationships
7. **Mengelola data akademik** melalui dashboard admin yang terintegrasi

---

## 📦 Prasyarat

> **⚠️ Penting:** Pastikan praktikum **Pertemuan 2** dan **Pertemuan 3** telah selesai sebelum memulai.

### Project & Database

| Komponen | Status |
|----------|--------|
| Project Laravel | ✅ Harus sudah ada |
| Database `akademik` | ✅ Harus sudah dibuat |
| Tabel `mahasiswa` | ✅ Harus sudah ada |
| Tabel `dosen` | ✅ Harus sudah ada |
| Tabel `matkul` | ✅ Harus sudah ada |
| Tabel `kelas_matkul` | ✅ Harus sudah ada |

### Authentication

| Komponen | Status |
|----------|--------|
| Laravel Breeze | ✅ Terinstall |
| Role user | ✅ Sudah ada kolom `role` di tabel `users` |
| Login & Dashboard | ✅ Berfungsi |

---

## ⚙️ Spesifikasi Teknologi

| Teknologi | Versi | Keterangan |
|-----------|-------|------------|
| **PHP** | 8.3 | Runtime bahasa pemrograman |
| **Laravel** | 13 | Framework PHP utama |
| **MySQL** | Latest | Database relasional |
| **Composer** | Latest | Dependency manager PHP |
| **NodeJS** | Latest | JavaScript runtime (untuk Breeze assets) |
| **Laravel Breeze** | Latest | Authentication scaffolding |
| **Laravel Filament** | 4 | Admin panel builder |

---

## 📂 Studi Kasus

### Sistem Informasi Akademik (SIA)

Aplikasi ini memungkinkan **admin** untuk mengelola seluruh data akademik melalui satu dashboard terpusat.

#### ✅ Admin Dapat Mengelola

- **Data Mahasiswa** — NIM, Nama, Program Studi
- **Data Dosen** — NIDN, Nama
- **Data Mata Kuliah** — Kode Matkul, Nama Matkul, SKS
- **Data Kelas Mata Kuliah** — Relasi Dosen + Matkul + Kelas

#### 🚫 Pembatasan Akses

- **Mahasiswa** → **TIDAK** dapat mengakses panel admin
- **Dosen** → **TIDAK** dapat mengakses panel admin
- Hanya user dengan `role === 'admin'` yang dapat masuk ke `/admin`

---

## ⏱ Alokasi Waktu

> **Total: 90 Menit**

| No | Kegiatan | Waktu |
|----|----------|-------|
| 1 | Instalasi Filament | 15 menit |
| 2 | Membuat Admin Panel | 10 menit |
| 3 | CRUD Mahasiswa | 15 menit |
| 4 | CRUD Dosen | 10 menit |
| 5 | CRUD Mata Kuliah | 10 menit |
| 6 | CRUD Kelas Matkul + Relasi | 20 menit |
| 7 | Pengujian | 10 menit |

---

## 💡 Apa itu Filament?

**[Filament](https://filamentphp.com)** adalah package Laravel yang menyediakan toolkit lengkap untuk membangun admin panel modern tanpa perlu menulis Blade secara manual.

### Fitur Utama

| Fitur | Deskripsi |
|-------|-----------|
| 📊 **Dashboard** | Widget dan statistik otomatis |
| 📝 **CRUD Otomatis** | Generate form & tabel dari satu resource file |
| 📋 **Form Input** | Komponen form lengkap (text, select, checkbox, dll) |
| 📊 **Tabel Data** | Sortable, searchable, filterable |
| 🔍 **Filter & Pencarian** | Built-in tanpa konfigurasi tambahan |
| 📈 **Statistik** | Widget stats otomatis |

### Keuntungan Menggunakan Filament

```
✅ Cepat         — Setup dalam hitungan menit
✅ Modern UI     — Tampilan profesional out-of-the-box
✅ No Blade      — Tidak perlu menulis template Blade manual
✅ Relasi DB     — Mendukung Eloquent relationships
✅ Extensible    — Mudah dikustomisasi dan diperluas
```

### Perbandingan: Tanpa Filament vs Dengan Filament

| Aspek | Tanpa Filament | Dengan Filament |
|-------|---------------|-----------------|
| CRUD 1 entitas | ~5-8 file (Controller, Model, Views, Routes) | 1 file Resource |
| Form | Buat Blade manual | Definisi di `form()` method |
| Tabel | Blade + pagination manual | Definisi di `table()` method |
| Search & Filter | Implementasi manual | Built-in method chaining |
| UI/UX | Design sendiri | Modern UI otomatis |
| Waktu development | Berjam-jam | Bermenit-menit |

---

## 📥 Instalasi Filament

### Step 1 — Masuk ke Folder Project

```bash
cd akademik
```

### Step 2 — Install Package Filament

```bash
composer require filament/filament
```

Perintah ini akan:
- Mendownload package Filament dari Packagist
- Menginstall semua dependency yang diperlukan
- Mendaftarkan service provider otomatis (auto-discovery)

### Step 3 — Install Panel Admin

```bash
php artisan filament:install --panels
```

Perintah ini akan:
- Membuat file konfigurasi `config/filament.php`
- Membuat `AdminPanelProvider` di `app/Providers/Filament/`
- Menambahkan route `/admin` secara otomatis
- Mempublish assets (CSS/JS) yang diperlukan

### Step 4 — Jalankan Migrasi

```bash
php artisan migrate
```

Memastikan semua tabel yang diperlukan Filament sudah terbuat di database.

---

## ▶️ Menjalankan Aplikasi

### Terminal

```bash
php artisan serve
```

### Akses Admin Panel

Buka browser dan navigasi ke:

```
http://127.0.0.1:8000/admin
```

> **📝 Catatan:** Pada tahap ini, halaman login Filament akan tampil tetapi belum ada akun admin yang bisa digunakan. Lanjut ke step berikutnya.

---

## 👤 Membuat User Admin Filament

### Generate User Admin

```bash
php artisan make:filament-user
```

### Input Data Admin

Saat diminta, masukkan data berikut:

| Field | Nilai |
|-------|-------|
| **Name** | `Administrator` |
| **Email** | `admin@kampus.ac.id` |
| **Password** | `admin12345` |

### Login

Buka `http://127.0.0.1:8000/admin` dan login menggunakan email & password yang sudah dibuat.

> **⚠️ Penting:** Untuk production, gunakan password yang kuat dan unik. `admin12345` hanya untuk keperluan praktikum.

---

## 🔐 Membatasi Akses Hanya Admin

Secara default, **semua user** yang terdaftar bisa login ke panel admin Filament. Kita perlu membatasi akses hanya untuk user dengan role `admin`.

### Implementasi

Buka file model User:

```
📁 app/Models/User.php
```

Tambahkan interface `FilamentUser` dan implementasi method `canAccessPanel()`:

```php
<?php

namespace App\Models;

use Illuminate\Foundation\Auth\User as Authenticatable;
use Illuminate\Notifications\Notifiable;
use Filament\Models\Contracts\FilamentUser;  // ← Tambahkan
use Filament\Panel;                          // ← Tambahkan

class User extends Authenticatable implements FilamentUser  // ← Tambahkan implements
{
    use Notifiable;

    // ... properti lainnya tetap ...

    /**
     * Menentukan apakah user bisa mengakses panel admin Filament.
     * Hanya user dengan role 'admin' yang diizinkan.
     */
    public function canAccessPanel(Panel $panel): bool
    {
        return $this->role === 'admin';
    }
}
```

### Penjelasan Kode

| Bagian | Penjelasan |
|--------|-----------|
| `FilamentUser` | Interface kontrak dari Filament yang mengharuskan implementasi method `canAccessPanel()` |
| `Panel $panel` | Parameter yang merepresentasikan panel Filament (bisa multi-panel) |
| `$this->role === 'admin'` | Mengecek apakah kolom `role` pada user bernilai `'admin'` |
| Return `true` | User diizinkan masuk panel admin |
| Return `false` | User ditolak, redirect ke halaman 403 |

### Alur Akses

```
User login ke /admin
       │
       ▼
canAccessPanel() dipanggil
       │
       ├── role === 'admin' → ✅ Masuk Dashboard
       │
       └── role !== 'admin' → 🚫 403 Forbidden
```

---

## 📋 CRUD Mahasiswa

### Step 1 — Generate Resource

```bash
php artisan make:filament-resource Mahasiswa
```

Perintah ini membuat beberapa file di `app/Filament/Resources/`:

```
📁 app/Filament/Resources/
├── MahasiswaResource.php           ← Resource utama (Form + Table)
└── MahasiswaResource/
    └── Pages/
        ├── CreateMahasiswa.php     ← Halaman tambah
        ├── EditMahasiswa.php       ← Halaman edit
        └── ListMahasiswas.php      ← Halaman daftar
```

### Step 2 — Definisi Form

Buka `app/Filament/Resources/MahasiswaResource.php` dan edit method `form()`:

```php
public static function form(Form $form): Form
{
    return $form
        ->schema([
            Forms\Components\TextInput::make('nim')
                ->required()
                ->unique(),

            Forms\Components\TextInput::make('nama')
                ->required(),

            Forms\Components\TextInput::make('prodi')
                ->required(),
        ]);
}
```

#### Penjelasan Komponen Form

| Method | Fungsi |
|--------|--------|
| `TextInput::make('nim')` | Membuat input teks untuk kolom `nim` |
| `->required()` | Field wajib diisi, validasi otomatis |
| `->unique()` | NIM harus unik, tidak boleh duplikat di database |

### Step 3 — Definisi Table

Edit method `table()` di file yang sama:

```php
public static function table(Table $table): Table
{
    return $table
        ->columns([
            Tables\Columns\TextColumn::make('nim')
                ->searchable(),

            Tables\Columns\TextColumn::make('nama')
                ->searchable(),

            Tables\Columns\TextColumn::make('prodi'),
        ]);
}
```

#### Penjelasan Komponen Table

| Method | Fungsi |
|--------|--------|
| `TextColumn::make('nim')` | Menampilkan kolom `nim` di tabel |
| `->searchable()` | Kolom bisa dicari melalui search bar |

### Hasil

Setelah konfigurasi, akses `http://127.0.0.1:8000/admin/mahasiswas` untuk melihat:
- **Tabel** data mahasiswa dengan pencarian
- **Tombol Create** untuk menambah data baru
- **Tombol Edit/Delete** pada setiap baris data

---

## 👨‍🏫 CRUD Dosen

### Generate Resource

```bash
php artisan make:filament-resource Dosen
```

### Form Schema

```php
public static function form(Form $form): Form
{
    return $form
        ->schema([
            Forms\Components\TextInput::make('nidn')
                ->required(),

            Forms\Components\TextInput::make('nama')
                ->required(),
        ]);
}
```

### Table Schema

```php
public static function table(Table $table): Table
{
    return $table
        ->columns([
            Tables\Columns\TextColumn::make('nidn'),

            Tables\Columns\TextColumn::make('nama'),
        ]);
}
```

> **💡 Tips:** Struktur resource Dosen mirip dengan Mahasiswa — perbedaan hanya di nama kolom (`nidn` vs `nim`).

---

## 📚 CRUD Mata Kuliah

### Generate Resource

```bash
php artisan make:filament-resource Matkul
```

### Form Schema

```php
public static function form(Form $form): Form
{
    return $form
        ->schema([
            Forms\Components\TextInput::make('kode_matkul'),

            Forms\Components\TextInput::make('nama_matkul'),

            Forms\Components\TextInput::make('sks')
                ->numeric(),
        ]);
}
```

### Table Schema

```php
public static function table(Table $table): Table
{
    return $table
        ->columns([
            Tables\Columns\TextColumn::make('kode_matkul'),

            Tables\Columns\TextColumn::make('nama_matkul'),

            Tables\Columns\TextColumn::make('sks'),
        ]);
}
```

#### Catatan Khusus

| Method | Penjelasan |
|--------|-----------|
| `->numeric()` | Validasi input hanya menerima angka. SKS harus berupa bilangan. |

---

## 🔗 Relasi Model

Sebelum membuat CRUD Kelas Matkul, kita perlu mendefinisikan **Eloquent Relationships** antar model.

### Diagram Relasi

```
┌──────────┐         ┌──────────────┐         ┌──────────┐
│  Dosen   │ 1 ──── N│ KelasMatkul  │N ──── 1 │  Matkul  │
│          │         │              │         │          │
│ - id     │         │ - id         │         │ - id     │
│ - nidn   │         │ - dosen_id   │         │ - kode   │
│ - nama   │         │ - matkul_id  │         │ - nama   │
│          │         │ - kelas      │         │ - sks    │
└──────────┘         └──────────────┘         └──────────┘
    hasMany              belongsTo              hasMany
                         belongsTo
```

### Model Dosen

```php
// 📁 app/Models/Dosen.php

public function kelas()
{
    return $this->hasMany(KelasMatkul::class);
}
```

**Penjelasan:** Satu dosen bisa mengajar di **banyak** kelas mata kuliah. Relasi **One-to-Many**.

### Model Matkul

```php
// 📁 app/Models/Matkul.php

public function kelas()
{
    return $this->hasMany(KelasMatkul::class);
}
```

**Penjelasan:** Satu mata kuliah bisa punya **banyak** kelas. Relasi **One-to-Many**.

### Model KelasMatkul

```php
// 📁 app/Models/KelasMatkul.php

public function dosen()
{
    return $this->belongsTo(Dosen::class);
}

public function matkul()
{
    return $this->belongsTo(Matkul::class);
}
```

**Penjelasan:**
- Setiap kelas matkul **dimiliki oleh** satu dosen → `belongsTo(Dosen::class)`
- Setiap kelas matkul **dimiliki oleh** satu matkul → `belongsTo(Matkul::class)`

### Ringkasan Tipe Relasi

| Model | Method | Relasi | Target |
|-------|--------|--------|--------|
| `Dosen` | `kelas()` | `hasMany` | `KelasMatkul` |
| `Matkul` | `kelas()` | `hasMany` | `KelasMatkul` |
| `KelasMatkul` | `dosen()` | `belongsTo` | `Dosen` |
| `KelasMatkul` | `matkul()` | `belongsTo` | `Matkul` |

---

## 🏫 CRUD Kelas Mata Kuliah

### Generate Resource

```bash
php artisan make:filament-resource KelasMatkul
```

### Form Schema — Menggunakan Select Relasi

```php
public static function form(Form $form): Form
{
    return $form
        ->schema([
            Forms\Components\Select::make('dosen_id')
                ->relationship('dosen', 'nama')
                ->required(),

            Forms\Components\Select::make('matkul_id')
                ->relationship('matkul', 'nama_matkul')
                ->required(),

            Forms\Components\TextInput::make('kelas')
                ->required(),
        ]);
}
```

#### Penjelasan Select Relationship

```php
Select::make('dosen_id')                    // Kolom foreign key di tabel
    ->relationship('dosen', 'nama')         // Nama relasi, kolom yang ditampilkan
    ->required();                           // Wajib dipilih
```

| Parameter | Nilai | Penjelasan |
|-----------|-------|-----------|
| `make()` | `'dosen_id'` | Nama kolom foreign key di tabel `kelas_matkul` |
| `relationship()` param 1 | `'dosen'` | Nama method relasi di model `KelasMatkul` |
| `relationship()` param 2 | `'nama'` | Kolom dari tabel `dosen` yang ditampilkan di dropdown |

Filament otomatis:
1. Membaca data dari tabel `dosen` melalui relasi
2. Menampilkannya sebagai dropdown `<select>`
3. Menyimpan `id` yang dipilih ke kolom `dosen_id`

### Table Schema — Menampilkan Data Relasi

```php
public static function table(Table $table): Table
{
    return $table
        ->columns([
            Tables\Columns\TextColumn::make('dosen.nama'),

            Tables\Columns\TextColumn::make('matkul.nama_matkul'),

            Tables\Columns\TextColumn::make('kelas'),
        ]);
}
```

#### Penjelasan Dot Notation

```php
TextColumn::make('dosen.nama')
//          └── relasi.kolom
```

Filament menggunakan **dot notation** untuk mengakses data dari model relasi:
- `dosen.nama` → Ambil kolom `nama` dari relasi `dosen()` di model `KelasMatkul`
- `matkul.nama_matkul` → Ambil kolom `nama_matkul` dari relasi `matkul()`

---

## 🎨 Navigation Icons

Tambahkan icon pada setiap resource agar menu navigasi dashboard lebih intuitif.

### Cara Menambahkan

Tambahkan property `$navigationIcon` di setiap file Resource:

```php
protected static ?string $navigationIcon = 'heroicon-o-academic-cap';
```

### Daftar Icon per Resource

| Resource | Icon | Heroicon |
|----------|------|----------|
| **Mahasiswa** | 👤 | `heroicon-o-user` |
| **Dosen** | 👨‍🏫 | `heroicon-o-user` |
| **Mata Kuliah** | 📖 | `heroicon-o-book-open` |
| **Kelas Matkul** | 🏫 | `heroicon-o-building-library` |

### Contoh Implementasi

```php
// 📁 app/Filament/Resources/MahasiswaResource.php

class MahasiswaResource extends Resource
{
    protected static ?string $model = Mahasiswa::class;

    protected static ?string $navigationIcon = 'heroicon-o-user';

    // ... form() dan table() ...
}
```

> **💡 Tips:** Daftar lengkap icon tersedia di [heroicons.com](https://heroicons.com). Gunakan prefix `heroicon-o-` untuk outline dan `heroicon-s-` untuk solid.

---

## 📊 Hasil Dashboard

Setelah semua resource dibuat, dashboard admin menampilkan menu navigasi:

```
┌─────────────────────────────────────┐
│  🏠 Dashboard                       │
│                                     │
│  📋 MENU                            │
│  ├── 👤 Mahasiswa                   │
│  ├── 👨‍🏫 Dosen                      │
│  ├── 📖 Mata Kuliah                 │
│  └── 🏫 Kelas Matkul               │
│                                     │
│  Setiap menu menyediakan:           │
│  ✅ Tambah data (Create)            │
│  ✅ Lihat daftar (Read/List)        │
│  ✅ Ubah data (Update/Edit)         │
│  ✅ Hapus data (Delete)             │
│  ✅ Pencarian (Search)              │
│  ✅ Tabel data (Sortable)           │
└─────────────────────────────────────┘
```

---

## ✅ Pengujian

| No | Pengujian | Hasil yang Diharapkan | Status |
|----|-----------|----------------------|--------|
| 1 | Login admin (`admin@kampus.ac.id`) | Masuk ke dashboard | ✅ Berhasil |
| 2 | Login dosen ke panel admin | Ditolak (403) | ✅ Berhasil (expected) |
| 3 | Tambah data mahasiswa | Data tersimpan, muncul di tabel | ✅ Berhasil |
| 4 | Edit data mahasiswa | Data terupdate | ✅ Berhasil |
| 5 | Hapus data mahasiswa | Data terhapus dari tabel | ✅ Berhasil |
| 6 | Tambah data dosen | Data tersimpan | ✅ Berhasil |
| 7 | Tambah data mata kuliah | Data tersimpan | ✅ Berhasil |
| 8 | Tambah data kelas matkul | Data tersimpan dengan relasi | ✅ Berhasil |
| 9 | Relasi dosen & matkul tampil | Nama dosen & matkul tampil di tabel kelas | ✅ Berhasil |

> **📝 Catatan Test #2:** Login dosen yang **ditolak** adalah **expected behavior** — membuktikan bahwa `canAccessPanel()` berfungsi dengan benar. Hanya role `admin` yang bisa masuk.

---

## 🖥️ Slide Presentasi

Materi ini dilengkapi dengan slide presentasi interaktif berbasis HTML/CSS/JS.

### Cara Menjalankan

Buka file `index.html` di browser:

```bash
open index.html
# atau double-click file index.html
```

### Fitur Slide

| Fitur | Cara Akses |
|-------|-----------|
| Navigasi maju | `→` / `Space` / Swipe kiri |
| Navigasi mundur | `←` / Swipe kanan |
| Overview semua slide | Tekan `O` |
| Fullscreen | Tekan `F` |
| Jump ke slide | Overview → klik slide |

### Fitur Interaktif

- **Demo Akses Admin** — Simulasi login dengan role berbeda (admin/dosen/mahasiswa)
- **Live CRUD Mahasiswa** — Tambah, edit, hapus, dan cari data secara real-time

---

## 🔧 Troubleshooting

### Filament tidak terinstall

```bash
# Pastikan PHP & Composer versi terbaru
php -v        # Harus >= 8.3
composer -V   # Harus terbaru

# Clear cache dan install ulang
composer clear-cache
composer require filament/filament
```

### Halaman /admin 404

```bash
# Pastikan panel terinstall
php artisan filament:install --panels

# Clear route cache
php artisan route:clear
php artisan config:clear
```

### User tidak bisa login

```bash
# Buat ulang user admin
php artisan make:filament-user

# Atau cek apakah user sudah ada
php artisan tinker
>>> User::where('email', 'admin@kampus.ac.id')->first()
```

### Relasi tidak tampil di tabel

Pastikan:
1. Method relasi sudah didefinisikan di model
2. Nama relasi di `TextColumn::make()` sesuai dengan nama method
3. Foreign key (`dosen_id`, `matkul_id`) ada di tabel `kelas_matkul`

```bash
# Cek struktur tabel
php artisan tinker
>>> Schema::getColumnListing('kelas_matkul')
```

---

## 📚 Referensi

| Resource | Link |
|----------|------|
| **Laravel Documentation** | [laravel.com/docs](https://laravel.com/docs) |
| **Filament Documentation** | [filamentphp.com/docs](https://filamentphp.com/docs) |
| **Eloquent Relationships** | [laravel.com/docs/eloquent-relationships](https://laravel.com/docs/eloquent-relationships) |
| **Heroicons** | [heroicons.com](https://heroicons.com) |
| **Filament Form Components** | [filamentphp.com/docs/forms](https://filamentphp.com/docs/forms) |
| **Filament Table Columns** | [filamentphp.com/docs/tables](https://filamentphp.com/docs/tables) |

---

## 📁 Struktur File Project (Setelah Praktikum)

```
akademik/
├── app/
│   ├── Filament/
│   │   └── Resources/
│   │       ├── MahasiswaResource.php
│   │       ├── MahasiswaResource/Pages/...
│   │       ├── DosenResource.php
│   │       ├── DosenResource/Pages/...
│   │       ├── MatkulResource.php
│   │       ├── MatkulResource/Pages/...
│   │       ├── KelasMatkulResource.php
│   │       └── KelasMatkulResource/Pages/...
│   ├── Models/
│   │   ├── User.php              ← + FilamentUser interface
│   │   ├── Mahasiswa.php
│   │   ├── Dosen.php             ← + hasMany(KelasMatkul)
│   │   ├── Matkul.php            ← + hasMany(KelasMatkul)
│   │   └── KelasMatkul.php       ← + belongsTo(Dosen, Matkul)
│   └── Providers/
│       └── Filament/
│           └── AdminPanelProvider.php
├── config/
│   └── filament.php
├── database/
│   └── migrations/...
└── ...
```

---

<div align="center">

**Dibuat untuk Praktikum Laravel — Semester 8**

*Selamat mengerjakan! 🚀*

</div>
