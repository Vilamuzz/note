# File Structure

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

Layered Structure mengorganisir code dalam bentuk layer seperti web, api, dan data. struktur ini membantu perhatian secara terpisah.

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

Domain Driven Design dipakai pada aplikasi besar yang cenderung setiap domain memiliki direktorinya masing masing.

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

Clean architecture menekankan perhatian terpisah antara layer yang berbeda pada aplikasi.

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

Mengorganisir kode ke dalam modul terpisah, setiap modul memiliki direktorinya masing masing, struktur ini berguna untuk mengembangkan komponen independen yang banyak pada satu proyek.

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
