<div align="center">

# Kilang Desa Murni Batik

**Platform E-Dagang Lengkap untuk Batik Malaysia**

*Full-stack e-commerce platform powering a traditional Malaysian batik factory's digital operations*

[![Services](https://img.shields.io/badge/Microservices-10-blue)]()
[![Frontend](https://img.shields.io/badge/Frontend_Apps-4-green)]()
[![Code](https://img.shields.io/badge/Lines_of_Code-250K+-orange)]()
[![API](https://img.shields.io/badge/API_Endpoints-800+-purple)]()
[![Docker](https://img.shields.io/badge/Docker_Containers-21-red)]()
[![DB Models](https://img.shields.io/badge/DB_Models-254-yellow)]()

**Direka, dibina, dan diurus sepenuhnya oleh seorang pembangun**

</div>

---

## Pembangun

| | |
|---|---|
| **Nama** | **Muhammad Luqman** |
| **Peranan** | Solo Full-Stack Developer & System Architect |
| **Skop** | Reka bentuk seni bina, pembangunan backend & frontend, reka bentuk pangkalan data, integrasi API luaran, DevOps & deployment, pengurusan infrastruktur |
| **Lokasi** | Terengganu, Malaysia |

> Keseluruhan platform ini — dari reka bentuk seni bina microservices, pembangunan 10 backend services dalam Go, 4 frontend apps dalam Next.js/TypeScript, reka bentuk 9 skema pangkalan data dengan 254 model, integrasi Shopee & TikTok API, sehingga deployment 21 Docker containers dalam production — dibina sepenuhnya secara solo oleh seorang pembangun.

---

## Tentang Projek

Kilang Desa Murni Batik ialah platform digital hujung-ke-hujung (*end-to-end*) yang menghubungkan kilang batik tradisional dengan pembeli moden. Sistem ini mengurus keseluruhan operasi perniagaan — dari pengurusan katalog produk, pemprosesan pesanan, penjejakan inventori, hingga integrasi marketplace seperti Shopee dan TikTok Shop.

Dibina dari awal menggunakan seni bina **perkhidmatan mikro (microservices)** dengan 10 backend services, 4 frontend apps, dan 21 Docker containers dalam production.

---

## Seni Bina Sistem

```mermaid
graph TB
    subgraph Clients["Pelanggan & Admin"]
        ST["Storefront<br/>(Kedai Online)"]
        AD["Admin Panel<br/>(Dashboard)"]
        AG["Agent Portal<br/>(Ejen Jualan)"]
        WH["Warehouse<br/>(Gudang)"]
    end

    subgraph Gateway["API Gateway"]
        NG["Nginx<br/>Reverse Proxy + SSL"]
    end

    subgraph Backend["Backend Microservices"]
        AUTH["Auth Service<br/>JWT & Sessions"]
        CAT["Catalog Service<br/>Produk & Kategori"]
        INV["Inventory Service<br/>Stok & Gudang"]
        ORD["Order Service<br/>Pesanan & Pembayaran"]
        CUST["Customer Service<br/>Pelanggan & CRM"]
        AGENT["Agent Service<br/>Ejen & Komisyen"]
        MKT["Marketplace Service<br/>Shopee & TikTok"]
        NOTIF["Notification Service<br/>Email & WhatsApp"]
        RPT["Reporting Service<br/>Laporan & Analitik"]
        SUP["Support Service<br/>Tiket Sokongan"]
    end

    subgraph Infrastructure["Infrastruktur"]
        PG[("PostgreSQL<br/>Database")]
        RD[("Redis<br/>Cache")]
        NATS["NATS<br/>Event Bus"]
        MINIO["MinIO<br/>Object Storage"]
        MS["Meilisearch<br/>Search Engine"]
        JG["Jaeger<br/>Tracing"]
    end

    subgraph External["Integrasi Luaran"]
        SHOPEE["Shopee API"]
        TIKTOK["TikTok Shop API"]
    end

    ST & AD & AG & WH --> NG
    NG --> AUTH & CAT & INV & ORD & CUST & AGENT & MKT & NOTIF & RPT & SUP

    AUTH & CAT & INV & ORD & CUST & AGENT & MKT & RPT & SUP --> PG
    CAT & INV & MKT --> RD
    CAT & INV & ORD & MKT --> NATS
    CAT --> MINIO
    CAT --> MS
    AUTH & CAT & ORD & MKT --> JG

    MKT --> SHOPEE & TIKTOK
```

---

## Ciri-Ciri Utama

### Kedai Online (Storefront)
| Ciri | Penerangan |
|------|------------|
| Katalog Produk | Paparan produk dengan carian pantas Meilisearch, penapis kategori & koleksi |
| Troli Beli-belah | Tambah ke troli, kemaskini kuantiti, checkout serta-merta |
| Pembayaran | Integrasi gateway pembayaran dengan penjejakan status |
| Akaun Pelanggan | Pendaftaran, log masuk, sejarah pesanan, alamat tersimpan |
| Responsif | Dioptimumkan untuk telefon bimbit dan desktop |

### Panel Admin (Dashboard)
| Ciri | Penerangan |
|------|------------|
| Pengurusan Pesanan | Lihat, proses, dan jejak semua pesanan dari semua saluran |
| Pengurusan Produk | CRUD produk, varian, imej, dan harga |
| Inventori | Penjejakan stok masa nyata, amaran stok rendah, pemindahan gudang |
| Pelanggan & CRM | Senarai pelanggan, sejarah pembelian, segmentasi |
| Laporan & Analitik | Jualan harian/bulanan, produk terlaris, prestasi ejen |
| Integrasi Shopee | Sambung kedai Shopee, segerak produk & pesanan automatik |
| Pengurusan Ejen | Daftar ejen, tetapkan komisyen, jejak prestasi |
| Sokongan Pelanggan | Sistem tiket untuk pertanyaan dan aduan |

### Integrasi Marketplace
| Ciri | Penerangan |
|------|------------|
| Shopee Open Platform | OAuth, segerak produk, segerak pesanan automatik setiap 15 minit |
| TikTok Shop | Integrasi API untuk pengurusan produk dan pesanan |
| Penyegerakan Stok | Kemas kini stok merentasi semua saluran jualan secara automatik |
| Pengurusan Token | Auto-refresh token OAuth sebelum tamat tempoh |

### Sistem Ejen
| Ciri | Penerangan |
|------|------------|
| Portal Ejen | Dashboard khusus untuk ejen membuat pesanan |
| Komisyen Automatik | Pengiraan dan penjejakan komisyen berdasarkan jualan |
| Katalog Ejen | Akses produk dengan harga ejen khas |

---

## Tech Stack

```mermaid
graph LR
    subgraph Backend
        GO["Go 1.23"]
        GIN["Gin Framework"]
        GORM["GORM ORM"]
    end

    subgraph Frontend
        NEXT["Next.js 15"]
        TS["TypeScript"]
        TW["Tailwind CSS"]
        SC["shadcn/ui"]
    end

    subgraph Database
        PG["PostgreSQL 16"]
        RD["Redis 7"]
        MS["Meilisearch"]
    end

    subgraph Infra
        DOCKER["Docker"]
        NATS["NATS"]
        MINIO["MinIO"]
        JAEGER["Jaeger"]
    end

    subgraph External
        SHOPEE["Shopee API"]
        TIKTOK["TikTok API"]
    end
```

| Lapisan | Teknologi | Tujuan |
|---------|-----------|--------|
| **Bahasa Backend** | Go 1.23 | Perkhidmatan mikro berprestasi tinggi |
| **Framework Web** | Gin | HTTP router & middleware |
| **ORM** | GORM | Interaksi pangkalan data |
| **Bahasa Frontend** | TypeScript | Keselamatan jenis (*type safety*) |
| **Framework UI** | Next.js 15 (App Router) | SSR, routing, API proxy |
| **Komponen UI** | shadcn/ui + Tailwind CSS | Antara muka pengguna moden |
| **Pangkalan Data** | PostgreSQL 16 | Data utama dengan skema khusus |
| **Cache** | Redis 7 | Cache sesi, analitik, token |
| **Carian** | Meilisearch | Carian produk pantas (*full-text*) |
| **Message Broker** | NATS | Komunikasi antara servis (event-driven) |
| **Storan Objek** | MinIO | Imej produk, dokumen |
| **Tracing** | Jaeger + OpenTelemetry | Penjejakan permintaan teragih |
| **Reverse Proxy** | Nginx | SSL termination, load balancing |
| **Kontena** | Docker Compose | Orkestrasi 21 kontena |

---

## Statistik Kod

```
  Jumlah Kod Sumber
  ═══════════════════════════════════════
  Backend (Go)         : 115,160 baris  │  493 fail
  Frontend (TypeScript): 135,836 baris  │  589 fail
  ─────────────────────────────────────
  JUMLAH               : 250,996 baris  │ 1,082 fail
```

### Backend — 10 Perkhidmatan Mikro

| Perkhidmatan | Baris Kod | Penerangan |
|-------------|-----------|------------|
| `service-catalog` | 28,526 | Pengurusan produk, kategori, koleksi, carian |
| `service-order` | 26,681 | Pesanan, pembayaran, penghantaran, aliran kerja |
| `service-marketplace` | 14,421 | Integrasi Shopee & TikTok, auto-sync |
| `service-inventory` | 10,924 | Stok, gudang, pemindahan, amaran |
| `service-auth` | 8,428 | Pengesahan JWT, sesi, peranan |
| `service-customer` | 7,625 | Profil pelanggan, alamat, CRM |
| `service-agent` | 7,044 | Ejen jualan, komisyen, pesanan ejen |
| `service-reporting` | 4,669 | Laporan jualan, analitik, eksport |
| `service-support` | 4,566 | Tiket sokongan, pertanyaan pelanggan |
| `service-notification` | 2,276 | Notifikasi email & mesej |

### Frontend — 4 Aplikasi

| Aplikasi | Baris Kod | Penerangan |
|----------|-----------|------------|
| `frontend-admin` | 74,007 | Panel pentadbir penuh |
| `frontend-storefront` | 54,325 | Kedai online pelanggan |
| `frontend-agent` | 3,981 | Portal ejen jualan |
| `frontend-warehouse` | 3,523 | Pengurusan gudang |

### Infrastruktur

| Komponen | Bilangan |
|----------|----------|
| API Endpoints | 800+ |
| Model Pangkalan Data | 254 |
| Docker Containers | 21 |
| Git Repositories | 22 |
| Skema PostgreSQL | `auth`, `catalog`, `inventory`, `sales`, `customer`, `agent`, `marketplace`, `support`, `reporting` |

---

## Reka Bentuk Pangkalan Data (Database Design)

Satu pangkalan data PostgreSQL dengan 9 skema berasingan — setiap perkhidmatan mikro memiliki skema sendiri untuk pengasingan data (*schema-per-service pattern*).

```mermaid
graph TB
    subgraph PostgreSQL["PostgreSQL 16 — kilang_batik"]
        subgraph auth_schema["auth"]
            AU_1["users"]
            AU_2["sessions"]
            AU_3["roles"]
            AU_4["permissions"]
            AU_5["password_resets"]
        end

        subgraph catalog_schema["catalog"]
            CA_1["products"]
            CA_2["product_variants"]
            CA_3["categories"]
            CA_4["collections"]
            CA_5["product_images"]
            CA_6["price_lists"]
            CA_7["product_tags"]
        end

        subgraph sales_schema["sales"]
            SA_1["orders"]
            SA_2["order_items"]
            SA_3["payments"]
            SA_4["shipments"]
            SA_5["order_status_history"]
            SA_6["refunds"]
            SA_7["order_addresses"]
        end

        subgraph inventory_schema["inventory"]
            IN_1["warehouses"]
            IN_2["stock_items"]
            IN_3["stock_movements"]
            IN_4["transfers"]
            IN_5["stock_alerts"]
        end

        subgraph customer_schema["customer"]
            CU_1["customers"]
            CU_2["addresses"]
            CU_3["customer_segments"]
            CU_4["customer_tags"]
        end

        subgraph agent_schema["agent"]
            AG_1["agents"]
            AG_2["agent_tiers"]
            AG_3["commissions"]
            AG_4["agent_orders"]
            AG_5["payouts"]
        end

        subgraph marketplace_schema["marketplace"]
            MK_1["connections"]
            MK_2["marketplace_products"]
            MK_3["marketplace_orders"]
            MK_4["marketplace_order_items"]
            MK_5["sync_logs"]
        end

        subgraph support_schema["support"]
            SU_1["tickets"]
            SU_2["ticket_replies"]
            SU_3["ticket_categories"]
        end

        subgraph reporting_schema["reporting"]
            RE_1["daily_sales"]
            RE_2["product_analytics"]
            RE_3["report_cache"]
        end
    end

    SA_1 -.->|"customer_id"| CU_1
    SA_1 -.->|"agent_id"| AG_1
    SA_2 -.->|"product_id"| CA_1
    SA_2 -.->|"variant_id"| CA_2
    IN_2 -.->|"variant_id"| CA_2
    AG_3 -.->|"order_id"| SA_1
    MK_3 -.->|"internal_order_id"| SA_1
    MK_2 -.->|"internal_product_id"| CA_1
```

### Ciri-Ciri Pangkalan Data

| Ciri | Penerangan |
|------|------------|
| Schema-per-Service | Setiap servis memiliki skema sendiri — pengasingan data yang jelas |
| Foreign Key Constraints | Rujukan silang antara skema untuk integriti data |
| Check Constraints | Pengesahan di peringkat DB (contoh: jumlah pesanan mesti positif) |
| Indeks Optimum | B-tree, GIN, dan partial indexes untuk prestasi query |
| UUID Primary Keys | Setiap rekod menggunakan UUID v4 — selamat untuk sistem teragih |
| Soft Deletes | Rekod tidak dipadam, hanya ditanda `deleted_at` |
| Audit Columns | `created_at`, `updated_at`, `created_by` pada setiap jadual |
| GORM AutoMigrate | Migrasi automatik semasa startup servis |

---

## Keselamatan (Security)

| Lapisan | Amalan |
|---------|--------|
| **Pengesahan** | JWT (access + refresh token) dengan sesi Redis |
| **Kata Laluan** | bcrypt hashing dengan cost factor 12 |
| **Kebenaran** | Role-Based Access Control (RBAC) — 5 peranan berlapis |
| **API Protection** | Auth middleware pada semua endpoint dilindungi |
| **Token OAuth** | Disulitkan (AES-256) sebelum disimpan dalam DB |
| **CORS** | Konfigurasi ketat — hanya domain dibenarkan |
| **Input Validation** | Pengesahan input pada setiap handler (Gin binding) |
| **SQL Injection** | Dicegah oleh GORM parameterized queries |
| **Rate Limiting** | Had kadar pada endpoint sensitif |
| **HTTPS** | SSL/TLS termination di Nginx (Let's Encrypt) |
| **Env Secrets** | Rahsia disimpan sebagai env vars, bukan dalam kod |

---

## Cabaran Teknikal & Penyelesaian

Beberapa cabaran teknikal utama yang diselesaikan semasa pembangunan platform ini:

### 1. Penyegerakan Pesanan Marketplace dengan Diskaun Shopee
**Masalah:** Shopee membenarkan baucar/diskaun yang menjadikan jumlah pesanan lebih rendah daripada jumlah item. Ini menyebabkan `shipping_cost` menjadi negatif dan melanggar *check constraint* dalam PostgreSQL.

**Penyelesaian:** Logik pintar dalam `CreateMarketplaceOrder` — apabila `TotalAmount < subtotal`, sistem mengira perbezaan sebagai `discount` dan menetapkan `shipping_cost = 0`, mengelakkan nilai negatif.

### 2. Seni Bina Event-Driven dengan NATS JetStream
**Masalah:** Servis perlu berkomunikasi secara asinkron tanpa saling bergantung (*loose coupling*). Contoh: apabila pesanan dicipta, inventori perlu dikemas kini dan notifikasi perlu dihantar — tanpa Order Service perlu tahu tentang kedua-dua servis tersebut.

**Penyelesaian:** Implement NATS JetStream sebagai event bus. Setiap servis menerbitkan (*publish*) event, dan servis lain melanggan (*subscribe*) secara bebas. 22+ jenis event merentasi sistem.

### 3. Pengurusan Token OAuth Shopee yang Tamat Tempoh
**Masalah:** Token OAuth Shopee tamat setiap 4 jam. Jika token tamat semasa auto-sync, semua operasi akan gagal.

**Penyelesaian:** Background token manager yang memeriksa token setiap 5 minit dan membaharui secara automatik 30 minit sebelum tamat tempoh — memastikan token sentiasa aktif.

### 4. Padanan SKU Merentasi Platform
**Masalah:** Produk di Shopee mempunyai SKU yang berbeza daripada sistem dalaman. Pesanan dari Shopee perlu dipautkan ke produk dalaman untuk penjejakan inventori.

**Penyelesaian:** Sistem padanan SKU dalam Marketplace Service yang memeta `external_sku` ke `internal_product_id` semasa penyegerakan produk, membolehkan penjejakan stok merentasi semua saluran.

### 5. Satu Pangkalan Data, 9 Skema Berasingan
**Masalah:** Bagaimana mengasingkan data untuk 10 perkhidmatan mikro tanpa menjalankan 10 pangkalan data berasingan (overhead terlalu tinggi untuk satu VPS).

**Penyelesaian:** Corak *schema-per-service* — satu pangkalan data PostgreSQL dengan 9 skema berasingan. Setiap servis hanya mengakses skemanya sendiri, tetapi masih boleh merujuk silang melalui foreign keys apabila perlu.

---

## Pemantauan & Kebolehpercayaan (Monitoring & Reliability)

```mermaid
graph LR
    subgraph Observability["Pemantauan"]
        LOG["Structured Logging<br/>(Zap JSON)"]
        TRACE["Distributed Tracing<br/>(OpenTelemetry → Jaeger)"]
        HEALTH["Health Checks<br/>(/health endpoint)"]
    end

    subgraph Reliability["Kebolehpercayaan"]
        GRACEFUL["Graceful Shutdown<br/>(signal handling)"]
        RESTART["Auto-Restart<br/>(Docker restart policy)"]
        RETRY["Retry Logic<br/>(HTTP clients)"]
    end

    subgraph Background["Proses Latar Belakang"]
        TOKEN["Token Manager<br/>(setiap 5 min)"]
        SYNC["Order Auto-Sync<br/>(setiap 15 min)"]
        CACHE["Analytics Cache<br/>(Redis TTL)"]
    end
```

| Ciri | Penerangan |
|------|------------|
| **Structured Logging** | Semua servis menggunakan Zap JSON logger — mudah dicari dan dianalisis |
| **Distributed Tracing** | OpenTelemetry + Jaeger — jejak permintaan merentasi semua servis |
| **Health Checks** | Setiap servis mendedahkan `/health` — Docker memeriksa secara berkala |
| **Graceful Shutdown** | Menangani signal OS (SIGTERM/SIGINT) — selesaikan permintaan aktif sebelum tutup |
| **Auto-Restart** | Docker `restart: unless-stopped` — servis pulih secara automatik selepas kegagalan |
| **Background Schedulers** | Token refresh (5 min), order auto-sync (15 min), analytics cache |
| **Error Recovery** | Retry logic pada panggilan HTTP antara servis dengan exponential backoff |

---

## Aliran Sistem (System Flows)

### 1. Pengesahan & Kebenaran (Authentication & Authorization)

Sistem pengesahan menggunakan JWT dengan sesi Redis. Setiap permintaan melalui middleware yang mengesahkan token dan memeriksa peranan pengguna.

```mermaid
sequenceDiagram
    participant U as Pengguna
    participant FE as Frontend App
    participant AUTH as Auth Service
    participant DB as PostgreSQL
    participant RD as Redis

    rect rgb(230, 245, 255)
    Note over U,RD: Pendaftaran Pengguna Baru
    U->>FE: Isi borang pendaftaran
    FE->>AUTH: POST /auth/register
    AUTH->>DB: Simpan pengguna (hash kata laluan)
    AUTH->>RD: Simpan sesi
    AUTH-->>FE: JWT token + refresh token
    FE-->>U: Berjaya log masuk
    end

    rect rgb(255, 243, 224)
    Note over U,RD: Log Masuk
    U->>FE: Masukkan email & kata laluan
    FE->>AUTH: POST /auth/login
    AUTH->>DB: Sahkan kredensial
    AUTH->>RD: Cipta sesi baru
    AUTH-->>FE: JWT token + refresh token
    end

    rect rgb(230, 255, 230)
    Note over FE,RD: Permintaan API Dilindungi
    FE->>AUTH: GET /api/... (Header: Bearer JWT)
    AUTH->>AUTH: Sahkan JWT + periksa peranan
    AUTH->>RD: Semak sesi aktif
    AUTH-->>FE: Data diminta
    end

    rect rgb(255, 230, 230)
    Note over FE,RD: Token Tamat Tempoh
    FE->>AUTH: POST /auth/refresh
    AUTH->>RD: Sahkan refresh token
    AUTH-->>FE: JWT token baru
    end
```

**Peranan pengguna:** `superadmin` → `admin` → `staff` → `agent` → `customer`

---

### 2. Katalog Produk (Product Catalog)

Pengurusan produk lengkap dengan sokongan varian, imej (MinIO), carian pantas (Meilisearch), dan penyegerakan automatik ke marketplace.

```mermaid
sequenceDiagram
    participant A as Admin
    participant FE as Admin Panel
    participant CAT as Catalog Service
    participant DB as PostgreSQL
    participant MIO as MinIO
    participant MS as Meilisearch
    participant NATS as NATS Event Bus
    participant MKT as Marketplace Service

    rect rgb(230, 245, 255)
    Note over A,MKT: Cipta Produk Baru
    A->>FE: Isi maklumat produk + muat naik imej
    FE->>CAT: POST /products (multipart)
    CAT->>MIO: Simpan imej produk
    MIO-->>CAT: URL imej
    CAT->>DB: Simpan produk + varian + harga
    CAT->>MS: Indeks ke Meilisearch
    CAT->>NATS: Publish: product.created
    NATS-->>MKT: Terima event
    MKT->>MKT: Segerak ke Shopee/TikTok
    CAT-->>FE: Produk berjaya dicipta
    end

    rect rgb(255, 243, 224)
    Note over A,MS: Kemas Kini Produk
    A->>FE: Edit maklumat / harga / stok
    FE->>CAT: PUT /products/:id
    CAT->>DB: Kemas kini rekod
    CAT->>MS: Kemas kini indeks carian
    CAT->>NATS: Publish: product.updated
    end

    rect rgb(230, 255, 230)
    Note over A,DB: Operasi Pukal (Bulk)
    A->>FE: Muat naik CSV
    FE->>CAT: POST /products/import
    CAT->>DB: Import produk secara pukal
    CAT-->>FE: Laporan import (berjaya/gagal)
    end
```

---

### 3. Pesanan Lengkap — Semua Saluran (Complete Order Flow)

Pesanan boleh datang dari 4 saluran berbeza: laman web, ejen jualan, admin manual, dan marketplace (Shopee/TikTok). Semua pesanan disatukan dalam satu sistem.

```mermaid
sequenceDiagram
    participant P as Pelanggan
    participant ST as Storefront
    participant AG as Agent Portal
    participant AD as Admin Panel
    participant SH as Shopee/TikTok
    participant MKT as Marketplace Service
    participant ORD as Order Service
    participant INV as Inventory Service
    participant NATS as NATS
    participant CAT as Catalog Service

    rect rgb(230, 245, 255)
    Note over P,NATS: Saluran 1: Pesanan Laman Web
    P->>ST: Checkout troli
    ST->>ORD: POST /orders
    ORD->>CAT: Sahkan produk & harga
    ORD->>INV: Tolak stok
    ORD->>NATS: Event: order.created
    ORD-->>ST: Order #KDM-20250208-001
    end

    rect rgb(255, 243, 224)
    Note over AG,NATS: Saluran 2: Pesanan Ejen
    AG->>ORD: POST /agent/orders
    ORD->>CAT: Sahkan produk & harga ejen
    ORD->>INV: Tolak stok
    ORD->>NATS: Event: order.created
    ORD-->>AG: Order + komisyen dikira
    end

    rect rgb(230, 255, 230)
    Note over AD,NATS: Saluran 3: Pesanan Manual Admin
    AD->>ORD: POST /admin/orders
    ORD->>INV: Tolak stok
    ORD->>NATS: Event: order.created
    end

    rect rgb(255, 230, 255)
    Note over SH,NATS: Saluran 4: Marketplace (Auto-Sync)
    SH-->>MKT: Pesanan baru di Shopee
    MKT->>MKT: Auto-sync setiap 15 minit
    MKT->>ORD: POST /orders/marketplace
    ORD->>INV: Tolak stok
    ORD->>NATS: Event: order.created
    end
```

---

### 4. Kitaran Hayat Pesanan (Order Lifecycle)

Setiap pesanan melalui beberapa status dari awal hingga selesai. Status boleh dikemas kini oleh admin, sistem, atau marketplace.

```mermaid
stateDiagram-v2
    [*] --> pending: Pesanan baru dicipta

    pending --> confirmed: Admin sahkan / Bayaran diterima
    pending --> cancelled: Pelanggan batal

    confirmed --> processing: Mula proses
    confirmed --> cancelled: Admin batal

    processing --> ready_to_ship: Barang dibungkus
    processing --> cancelled: Admin batal

    ready_to_ship --> shipped: Kurier kutip barang
    shipped --> delivered: Pelanggan terima

    delivered --> completed: Selesai
    delivered --> return_requested: Pelanggan mohon pulang

    return_requested --> returned: Barang dipulangkan
    returned --> refunded: Wang dikembalikan

    cancelled --> refunded: Wang dikembalikan (jika sudah bayar)

    completed --> [*]
    refunded --> [*]
```

---

### 5. Inventori & Gudang (Inventory & Warehouse)

Pengurusan stok masa nyata merentasi pelbagai gudang. Stok ditolak apabila pesanan disahkan dan dipulihkan apabila dibatalkan.

```mermaid
sequenceDiagram
    participant ORD as Order Service
    participant NATS as NATS Event Bus
    participant INV as Inventory Service
    participant DB as PostgreSQL
    participant MKT as Marketplace Service
    participant SH as Shopee

    rect rgb(230, 245, 255)
    Note over ORD,DB: Tolak Stok (Pesanan Disahkan)
    ORD->>NATS: Event: order.confirmed
    NATS-->>INV: Terima event
    INV->>DB: Tolak stok varian dari gudang
    INV->>DB: Rekod pergerakan stok
    INV->>NATS: Event: inventory.stock.changed
    NATS-->>MKT: Terima event
    MKT->>SH: Kemas kini stok di Shopee
    end

    rect rgb(255, 230, 230)
    Note over ORD,DB: Pulih Stok (Pesanan Dibatalkan)
    ORD->>NATS: Event: order.cancelled
    NATS-->>INV: Terima event
    INV->>DB: Pulihkan stok varian
    INV->>DB: Rekod pergerakan stok
    INV->>NATS: Event: inventory.stock.changed
    end

    rect rgb(255, 243, 224)
    Note over INV,DB: Amaran Stok Rendah
    INV->>DB: Semak paras stok
    INV->>INV: Stok bawah minimum?
    INV->>NATS: Event: inventory.low_stock
    end

    rect rgb(230, 255, 230)
    Note over INV,DB: Pemindahan Antara Gudang
    INV->>DB: Tolak stok dari Gudang A
    INV->>DB: Tambah stok ke Gudang B
    INV->>DB: Rekod pemindahan
    end
```

---

### 6. Integrasi Marketplace — Shopee & TikTok

Integrasi penuh dengan Shopee Open Platform dan TikTok Shop API termasuk OAuth, penyegerakan produk, pesanan automatik, dan pengurusan token.

```mermaid
sequenceDiagram
    participant A as Admin
    participant FE as Admin Panel
    participant MKT as Marketplace Service
    participant SH as Shopee API
    participant DB as PostgreSQL
    participant RD as Redis
    participant ORD as Order Service

    rect rgb(230, 245, 255)
    Note over A,DB: Sambungan OAuth
    A->>FE: Klik "Sambung Shopee"
    FE->>MKT: GET /connections/shopee/auth-url
    MKT-->>FE: URL OAuth Shopee
    FE->>SH: Redirect ke Shopee login
    SH-->>MKT: Callback dengan auth code
    MKT->>SH: Tukar code → access token
    MKT->>DB: Simpan token (encrypted)
    end

    rect rgb(255, 243, 224)
    Note over MKT,SH: Segerak Produk
    A->>FE: Klik "Sync Products"
    FE->>MKT: POST /connections/:id/sync/products
    MKT->>SH: GET /product/get_item_list
    MKT->>DB: Simpan/kemas kini produk
    MKT-->>FE: 150 produk disegerakkan
    end

    rect rgb(230, 255, 230)
    Note over MKT,ORD: Auto-Sync Pesanan (Setiap 15 Minit)
    MKT->>MKT: Background scheduler tick
    MKT->>SH: GET /order/get_order_list
    SH-->>MKT: Senarai pesanan baru
    loop Setiap pesanan baru
        MKT->>DB: Simpan ke marketplace DB
        MKT->>ORD: POST /orders/marketplace
        ORD-->>MKT: Order ID dalaman
        MKT->>DB: Simpan internal_order_id
    end
    end

    rect rgb(255, 230, 255)
    Note over MKT,RD: Auto-Refresh Token (Setiap 5 Minit)
    MKT->>MKT: Token manager check
    MKT->>DB: Cari token hampir tamat
    MKT->>SH: POST /auth/token/get (refresh)
    MKT->>DB: Kemas kini token baru
    end
```

---

### 7. Pelanggan & CRM (Customer Management)

Pengurusan data pelanggan dari pelbagai saluran — storefront, ejen, dan admin manual.

```mermaid
sequenceDiagram
    participant P as Pelanggan
    participant ST as Storefront
    participant AD as Admin Panel
    participant CUST as Customer Service
    participant DB as PostgreSQL
    participant ORD as Order Service

    rect rgb(230, 245, 255)
    Note over P,DB: Pendaftaran Pelanggan
    P->>ST: Daftar akaun baru
    ST->>CUST: POST /customers/register
    CUST->>DB: Cipta profil pelanggan
    CUST-->>ST: Akaun berjaya
    end

    rect rgb(255, 243, 224)
    Note over P,DB: Pengurusan Alamat
    P->>ST: Tambah alamat penghantaran
    ST->>CUST: POST /customers/:id/addresses
    CUST->>DB: Simpan alamat
    P->>ST: Tetapkan alamat utama
    ST->>CUST: PUT /customers/:id/addresses/:aid/default
    end

    rect rgb(230, 255, 230)
    Note over AD,ORD: CRM — Sejarah Pelanggan
    AD->>CUST: GET /admin/customers/:id
    CUST->>DB: Profil + alamat + segmen + tag
    AD->>ORD: GET /admin/orders?customer_id=xxx
    ORD-->>AD: Sejarah pesanan pelanggan
    AD->>AD: Paparan lengkap pelanggan
    end

    rect rgb(255, 230, 255)
    Note over AD,DB: Import Pukal
    AD->>CUST: POST /admin/customers/import (CSV)
    CUST->>DB: Import pelanggan secara pukal
    CUST-->>AD: Laporan import
    end
```

---

### 8. Sistem Ejen Jualan (Sales Agent System)

Ejen jualan berdaftar melalui admin dan boleh membuat pesanan bagi pihak pelanggan. Komisyen dikira secara automatik.

```mermaid
sequenceDiagram
    participant AD as Admin
    participant AGP as Agent Portal
    participant AGT as Agent Service
    participant ORD as Order Service
    participant DB as PostgreSQL

    rect rgb(230, 245, 255)
    Note over AD,DB: Daftar & Urus Ejen
    AD->>AGT: POST /admin/agents (daftar ejen baru)
    AGT->>DB: Cipta profil ejen + kadar komisyen
    AD->>AGT: PUT /admin/agents/:id/tier (tetapkan tier)
    AGT->>DB: Kemas kini tier & kadar
    end

    rect rgb(255, 243, 224)
    Note over AGP,DB: Ejen Buat Pesanan
    AGP->>AGT: POST /agent/orders
    AGT->>ORD: Cipta pesanan (source: agent)
    ORD-->>AGT: Order ID
    AGT->>DB: Kira komisyen automatik
    AGT->>DB: Rekod komisyen (pending)
    AGT-->>AGP: Pesanan + komisyen dikira
    end

    rect rgb(230, 255, 230)
    Note over AD,DB: Laporan Prestasi Ejen
    AD->>AGT: GET /admin/agents/:id/performance
    AGT->>DB: Jumlah jualan, komisyen, pesanan
    AGT-->>AD: Dashboard prestasi ejen
    end

    rect rgb(255, 230, 255)
    Note over AD,DB: Bayar Komisyen
    AD->>AGT: POST /admin/commissions/batch-pay
    AGT->>DB: Kemas kini status: pending → paid
    end
```

---

### 9. Sokongan & Tiket (Support Tickets)

Sistem tiket untuk menguruskan pertanyaan dan aduan pelanggan.

```mermaid
sequenceDiagram
    participant P as Pelanggan
    participant ST as Storefront
    participant AD as Admin Panel
    participant SUP as Support Service
    participant DB as PostgreSQL

    rect rgb(230, 245, 255)
    Note over P,DB: Cipta Tiket Baru
    P->>ST: Isi borang aduan/pertanyaan
    ST->>SUP: POST /tickets
    SUP->>DB: Simpan tiket (status: open)
    SUP-->>ST: Tiket #TIK-001
    end

    rect rgb(255, 243, 224)
    Note over AD,DB: Admin Respon
    AD->>SUP: GET /admin/tickets (senarai tiket)
    SUP-->>AD: Senarai tiket terbuka
    AD->>SUP: POST /admin/tickets/:id/replies
    SUP->>DB: Simpan balasan + kemas kini status
    SUP->>DB: Status: open → in_progress
    end

    rect rgb(230, 255, 230)
    Note over AD,DB: Selesai & Tutup
    AD->>SUP: PUT /admin/tickets/:id/status
    SUP->>DB: Status: in_progress → resolved
    P->>ST: Sahkan penyelesaian
    ST->>SUP: PUT /tickets/:id/close
    SUP->>DB: Status: resolved → closed
    end
```

---

### 10. Laporan & Analitik (Reporting & Analytics)

Dashboard analitik masa nyata untuk pemantauan prestasi perniagaan.

```mermaid
sequenceDiagram
    participant AD as Admin Panel
    participant RPT as Reporting Service
    participant ORD as Order Service
    participant INV as Inventory Service
    participant AGT as Agent Service
    participant DB as PostgreSQL

    rect rgb(230, 245, 255)
    Note over AD,DB: Dashboard Utama
    AD->>RPT: GET /admin/dashboard
    RPT->>DB: Jualan hari ini / minggu / bulan
    RPT->>DB: Pesanan mengikut status
    RPT->>DB: Produk terlaris
    RPT->>DB: Jumlah pelanggan baru
    RPT-->>AD: Data dashboard lengkap
    end

    rect rgb(255, 243, 224)
    Note over AD,DB: Laporan Jualan
    AD->>RPT: GET /admin/reports/sales?from=...&to=...
    RPT->>DB: Agregat jualan mengikut tempoh
    RPT->>DB: Pecahan mengikut saluran
    RPT-->>AD: Laporan jualan + carta
    end

    rect rgb(230, 255, 230)
    Note over AD,DB: Eksport Data
    AD->>RPT: GET /admin/reports/export?format=csv
    RPT->>DB: Jana data laporan
    RPT-->>AD: Fail CSV dimuat turun
    end
```

---

### 11. Komunikasi Antara Servis (Inter-Service Communication)

Peta lengkap komunikasi antara semua perkhidmatan mikro melalui NATS Event Bus dan panggilan HTTP langsung.

```mermaid
graph TB
    subgraph NATS_Events["NATS Event Bus"]
        direction TB
        E1["order.created"]
        E2["order.confirmed"]
        E3["order.cancelled"]
        E4["order.status.updated"]
        E5["product.created"]
        E6["product.updated"]
        E7["product.deleted"]
        E8["inventory.stock.changed"]
        E9["inventory.low_stock"]
        E10["inventory.transfer.completed"]
        E11["customer.registered"]
        E12["payment.received"]
    end

    subgraph Publishers["Penerbit (Publishers)"]
        ORD_P["Order Service"]
        CAT_P["Catalog Service"]
        INV_P["Inventory Service"]
        CUST_P["Customer Service"]
    end

    subgraph Subscribers["Pelanggan (Subscribers)"]
        INV_S["Inventory Service"]
        MKT_S["Marketplace Service"]
        NOTIF_S["Notification Service"]
        RPT_S["Reporting Service"]
    end

    ORD_P -->|order.*| E1 & E2 & E3 & E4
    CAT_P -->|product.*| E5 & E6 & E7
    INV_P -->|inventory.*| E8 & E9 & E10
    CUST_P -->|customer.*| E11

    E2 & E3 -->|stok| INV_S
    E5 & E6 & E7 -->|sync produk| MKT_S
    E8 -->|sync stok| MKT_S
    E1 & E12 -->|notifikasi| NOTIF_S
    E1 & E2 & E3 -->|laporan| RPT_S
```

#### Panggilan HTTP Antara Servis

```mermaid
graph LR
    ORD["Order Service"]
    CAT["Catalog Service"]
    INV["Inventory Service"]
    AGT["Agent Service"]
    MKT["Marketplace Service"]
    CUST["Customer Service"]

    ORD -->|"Sahkan produk & harga"| CAT
    ORD -->|"Tolak/pulih stok"| INV
    ORD -->|"Sahkan pelanggan"| CUST
    AGT -->|"Cipta pesanan ejen"| ORD
    MKT -->|"Cipta pesanan marketplace"| ORD
    MKT -->|"Padankan SKU → produk"| CAT
    MKT -->|"Segerak stok"| INV
```

---

### 12. Aliran Pengguna — Kedai Online (Storefront User Journey)

Perjalanan pengguna lengkap dari melayari kedai sehingga pesanan selesai.

```mermaid
graph TB
    subgraph Pelayaran["Pelayaran Kedai"]
        HOME["Laman Utama"] --> BROWSE["Layari Kategori"]
        HOME --> SEARCH["Carian Produk"]
        HOME --> COLL["Lihat Koleksi"]
        BROWSE --> PDP["Halaman Produk"]
        SEARCH --> PDP
        COLL --> PDP
    end

    subgraph Pembelian["Proses Pembelian"]
        PDP --> VARIANT["Pilih Varian & Kuantiti"]
        VARIANT --> CART["Tambah ke Troli"]
        CART --> CHECKOUT["Checkout"]
        CHECKOUT --> ADDRESS["Pilih Alamat"]
        ADDRESS --> PAY["Pembayaran"]
        PAY --> CONFIRM["Pengesahan Pesanan"]
    end

    subgraph Pengurusan["Pengurusan Akaun"]
        LOGIN["Log Masuk / Daftar"]
        PROFILE["Profil Saya"]
        ADDR_MGMT["Urus Alamat"]
        ORDER_HIST["Sejarah Pesanan"]
        TRACK["Jejak Pesanan"]
        TICKET["Buka Tiket Sokongan"]

        LOGIN --> PROFILE
        PROFILE --> ADDR_MGMT
        PROFILE --> ORDER_HIST
        ORDER_HIST --> TRACK
        ORDER_HIST --> TICKET
    end

    CONFIRM --> ORDER_HIST
```

---

### 13. Aliran Pengguna — Panel Admin (Admin Dashboard Journey)

Gambaran keseluruhan modul dalam panel pentadbir yang menguruskan semua aspek perniagaan.

```mermaid
graph TB
    subgraph Dashboard["Dashboard Utama"]
        DASH["Ringkasan Jualan & Pesanan"]
    end

    subgraph Produk["Pengurusan Produk"]
        PROD_LIST["Senarai Produk"]
        PROD_ADD["Tambah Produk"]
        PROD_EDIT["Edit Produk & Varian"]
        CAT_MGMT["Kategori & Koleksi"]
        PROD_LIST --> PROD_ADD
        PROD_LIST --> PROD_EDIT
        PROD_LIST --> CAT_MGMT
    end

    subgraph Pesanan["Pengurusan Pesanan"]
        ORD_LIST["Senarai Pesanan"]
        ORD_DETAIL["Butiran Pesanan"]
        ORD_STATUS["Kemas Kini Status"]
        ORD_MANUAL["Cipta Pesanan Manual"]
        ORD_LIST --> ORD_DETAIL
        ORD_DETAIL --> ORD_STATUS
        ORD_LIST --> ORD_MANUAL
    end

    subgraph Inventori["Inventori & Gudang"]
        STOCK["Tahap Stok"]
        WAREHOUSE["Urus Gudang"]
        TRANSFER["Pemindahan Stok"]
        ALERTS["Amaran Stok Rendah"]
        STOCK --> TRANSFER
        STOCK --> ALERTS
        STOCK --> WAREHOUSE
    end

    subgraph Pelanggan["Pelanggan & CRM"]
        CUST_LIST["Senarai Pelanggan"]
        CUST_DETAIL["Profil Pelanggan"]
        CUST_SEG["Segmen & Tag"]
        CUST_IMPORT["Import CSV"]
        CUST_LIST --> CUST_DETAIL
        CUST_LIST --> CUST_SEG
        CUST_LIST --> CUST_IMPORT
    end

    subgraph Marketplace["Integrasi Marketplace"]
        MKT_CONN["Sambungan Shopee/TikTok"]
        MKT_PROD["Segerak Produk"]
        MKT_ORD["Segerak Pesanan"]
        MKT_ANALYTICS["Analitik Marketplace"]
        MKT_CONN --> MKT_PROD
        MKT_CONN --> MKT_ORD
        MKT_CONN --> MKT_ANALYTICS
    end

    subgraph Ejen["Pengurusan Ejen"]
        AGT_LIST["Senarai Ejen"]
        AGT_COMM["Komisyen & Pembayaran"]
        AGT_PERF["Prestasi Ejen"]
        AGT_LIST --> AGT_COMM
        AGT_LIST --> AGT_PERF
    end

    subgraph Laporan["Laporan & Analitik"]
        RPT_SALES["Jualan Harian/Bulanan"]
        RPT_PRODUCT["Prestasi Produk"]
        RPT_EXPORT["Eksport CSV"]
        RPT_SALES --> RPT_EXPORT
        RPT_PRODUCT --> RPT_EXPORT
    end

    subgraph Sokongan["Sokongan Pelanggan"]
        TIK_LIST["Senarai Tiket"]
        TIK_REPLY["Balas Tiket"]
        TIK_LIST --> TIK_REPLY
    end

    DASH --> Produk
    DASH --> Pesanan
    DASH --> Inventori
    DASH --> Pelanggan
    DASH --> Marketplace
    DASH --> Ejen
    DASH --> Laporan
    DASH --> Sokongan
```

---

## Deployment

Semua servis dijalankan dalam Docker containers pada satu VPS dengan konfigurasi Docker Compose.

```
  Production Infrastructure
  ════════════════════════════════════════
  Server         : 1x VPS (Linux)
  Containers     : 21 Docker containers
  Orchestration  : Docker Compose
  Reverse Proxy  : Nginx + SSL (Let's Encrypt)
  Database       : PostgreSQL 16 (9 schemas)
  Cache          : Redis 7
  Search         : Meilisearch
  Event Bus      : NATS JetStream
  Object Storage : MinIO
  Tracing        : Jaeger + OpenTelemetry
```

| Ciri Operasi | Penerangan |
|-------------|------------|
| Health Checks | Setiap servis mendedahkan `/health` — Docker memeriksa berkala |
| Structured Logging | JSON logging (Zap) — mudah dicari dan debug |
| Distributed Tracing | OpenTelemetry → Jaeger — jejak permintaan merentasi servis |
| Graceful Shutdown | Signal handling (SIGTERM) — selesaikan permintaan sebelum tutup |
| Auto-Restart | `restart: unless-stopped` — pulih automatik selepas kegagalan |
| Background Jobs | Token refresh (5 min), order sync (15 min), analytics cache |

---

<div align="center">

**Direka & dibina sepenuhnya oleh Muhammad Luqman**

Solo Full-Stack Developer & System Architect

*Go, Next.js, PostgreSQL, Docker, dan semangat batik Malaysia*

Terengganu, Malaysia

</div>
