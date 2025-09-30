# File Structure

Ref: https://gist.github.com/ayoubzulfiqar/9f1a34049332711fddd4d4b2bfd46096

## 1. Common

```go
project-root/
    ├── cmd/
    │   ├── your-app-name/
    │   │   ├── main.go         # Application entry point
    │   │   └── ...             # Other application-specific files
    │   └── another-app/
    │       ├── main.go         # Another application entry point
    │       └── ...
    ├── internal/                # Private application and package code
    │   ├── config/
    │   │   ├── config.go       # Configuration logic
    │   │   └── ...
    │   ├── database/
    │   │   ├── database.go     # Database setup and access
    │   │   └── ...
    │   └── ...
    ├── pkg/                     # Public, reusable packages
    │   ├── mypackage/
    │   │   ├── mypackage.go    # Public package code
    │   │   └── ...
    │   └── ...
    ├── api/                     # API-related code (e.g., REST or gRPC)
    │   ├── handler/
    │   │   ├── handler.go      # HTTP request handlers
    │   │   └── ...
    │   ├── middleware/
    │   │   ├── middleware.go  # Middleware for HTTP requests
    │   │   └── ...
    │   └── ...
    ├── web/                     # Front-end web application assets
    │   ├── static/
    │   │   ├── css/
    │   │   ├── js/
    │   │   └── ...
    │   └── templates/
    │       ├── index.html
    │       └── ...
    ├── scripts/                 # Build, deployment, and maintenance scripts
    │   ├── build.sh
    │   ├── deploy.sh
    │   └── ...
    ├── configs/                 # Configuration files for different environments
    │   ├── development.yaml
    │   ├── production.yaml
    │   └── ...
    ├── tests/                   # Unit and integration tests
    │   ├── unit/
    │   │   ├── ...
    │   └── integration/
    │       ├── ...
    ├── docs/                    # Project documentation
    ├── .gitignore               # Gitignore file
    ├── go.mod                   # Go module file
    ├── go.sum                   # Go module dependencies file
    └── README.md                # Project README
```

- cmd/: Berisi entry point utama aplikasi. Setiap sub-folder di dalamnya adalah satu aplikasi yang bisa dieksekusi, dengan file main.go sebagai starternya.

- internal/: Berisi kode privat aplikasi. Go secara paksa akan mencegah package lain di luar proyek ini mengimpor kode dari direktori internal. Ideal untuk logika bisnis inti yang tidak ingin diekspos ke luar.

- pkg/: Berisi package publik yang dapat digunakan kembali (reusable) oleh proyek eksternal. Jika Anda membuat sebuah library yang ingin dibagikan kepada orang lain, letakkan di sini.

- api/: Menampung semua kode yang terkait dengan definisi dan logika API, seperti file skema (misalnya, OpenAPI, gRPC proto), request handler, dan middleware.

- web/: Digunakan untuk aset aplikasi front-end, seperti file static (CSS, JavaScript, gambar) dan file template HTML, jika Anda menyajikan web langsung dari aplikasi Go Anda.

- scripts/: Berisi berbagai skrip untuk mengotomatiskan tugas-tugas proyek, seperti proses build, deployment, atau migrasi database. Contohnya: build.sh atau deploy.sh.

- configs/: Menyimpan file konfigurasi untuk berbagai lingkungan (environment) seperti development, staging, dan production. Contohnya config.dev.yaml.

- docs/: Berisi semua dokumentasi proyek, baik untuk pengguna maupun developer. Contohnya adalah panduan penggunaan, dokumentasi arsitektur, atau spesifikasi API.

## 2. Flat Structure

Flat Structure cocok digunakan untuk proyek berskala kecil, karakter dari struktur ini adalah semua file go yang bersebelahan di directori root proyek, sturktur ini membuat terlihat sederhana namun akan sulit manajemen ketika proyek bertumbuh.

```go
project-root/
    ├── main.go
    ├── handler.go
    ├── config.go
    ├── database.go
    ├── ...
    ├── static/
    ├── templates/
    ├── scripts/
    ├── configs/
    ├── tests/
    └── docs/
```

## 3. Layered Structure

Layered Structure mengorganisir kode dalam bentuk layer seperti web, api, dan data. setiap layer memiliki tanggung jawab yang berbeda membuat struktur ini dapat dikelola dengan perhatian secara terpisah.

- Presentation Layer (web/, api/): Bertanggung jawab untuk menangani HTTP request, response, dan routing.

- Business Logic Layer (service/, usecase/): Berisi logika bisnis inti dari aplikasi.

- Data Access Layer (data/, repository/): Bertanggung jawab untuk berkomunikasi dengan database (membaca/menulis data).

Struktur ini membantu memisahkan "apa yang dilihat pengguna" dari "logika bisnis" dan "cara penyimpanan data".

```go
project-root/
    ├── main.go
    ├── web/
    │   ├── handler.go
    │   ├── static/
    │   ├── templates/
    ├── api/
    │   ├── routes.go
    │   ├── middleware/
    ├── data/
    │   ├── database.go
    │   ├── repository.go
    ├── configs/
    ├── tests/
    ├── docs/
```

## 4. Domain Driven Design

Domain Driven Design berfokus pada domain bisnis, bukan layer teknis. Kode diorganisir berdasarkan fitur atau konteks bisnis, seperti auth/ (autentikasi), orders/ (pesanan), atau products/ (produk). Setiap folder domain ini berisi semua yang dibutuhkannya (handler, service, repository). Cocok untuk aplikasi yang sangat kompleks di mana logika bisnisnya rumit dan spesifik.

```go
project-root/
    ├── cmd/
    │   ├── app1/
    │   ├── app2/
    ├── internal/
    │   ├── auth/
    │   │   ├── handler.go
    │   │   ├── service.go
    │   ├── orders/
    │   │   ├── handler.go
    │   │   ├── service.go
    │   ├── ...
    ├── pkg/
    │   ├── utility/
    │   │   ├── ...
    │   ├── ...
    ├── api/
    │   ├── app1/
    │   │   ├── ...
    │   ├── app2/
    │   │   ├── ...
    ├── web/
    │   ├── app1/
    │   │   ├── ...
    │   ├── app2/
    │   │   ├── ...
    ├── scripts/
    ├── configs/
    ├── tests/
    └── docs/
```

## 5. Clean Architecture

Clean architecture merupakan evolusi dari Layered Structure dengan aturan ketergantungan yang sangat ketat. Aturannya adalah: "Ketergantungan hanya boleh mengarah ke dalam".

- Inti/Terdalam (domain/entities): Berisi model data dan aturan bisnis paling dasar. Layer ini tidak boleh bergantung pada apapun.
- Layer Luar: Berisi detail teknis seperti database, framework web, atau UI. Layer ini bergantung pada layer inti, tetapi tidak sebaliknya.
  Tujuannya adalah agar logika bisnis inti terisolasi dan tidak terpengaruh oleh perubahan teknologi (misalnya, mengganti database dari PostgreSQL ke MongoDB).

```go
project-root/
    ├── cmd/
    │   ├── your-app/
    │   │   ├── main.go
    ├── internal/
    │   ├── app/
    │   │   ├── handler.go
    │   │   ├── service.go
    │   ├── domain/
    │   │   ├── model.go
    │   │   ├── repository.go
    ├── pkg/
    │   ├── utility/
    │   │   ├── ...
    ├── api/
    │   ├── ...
    ├── web/
    │   ├── ...
    ├── scripts/
    ├── configs/
    ├── tests/
    └── docs/
```

## 6. Modular Structure

Sturktur modular digunakan untuk mengelola beberapa aplikasi atau layanan yang (idealnya) independen dalam satu repository tunggal (monorepo). Setiap modul (module1/, module2/) bisa dianggap sebagai proyek kecil yang memiliki strukturnya sendiri. Struktur ini sangat berguna untuk tim besar di mana setiap tim kecil bertanggung jawab atas modul atau layanan yang berbeda.

```go
project-root/
    ├── module1/
    │   ├── cmd/
    │   ├── internal/
    │   ├── pkg/
    │   ├── api/
    │   ├── web/
    │   ├── scripts/
    │   ├── configs/
    │   ├── tests/
    │   └── docs/
    ├── module2/
    │   ├── ...
```
