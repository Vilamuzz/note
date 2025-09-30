# Framework Go

## Gin

Gin adalah framework web yang cepat, minimalis, dan memiliki performa tinggi. Ia terkenal karena routing-nya yang efisien dan penggunaan middleware yang mudah. Gin sangat populer untuk membangun API REST karena kesederhanaan dan kecepatannya.

## Fiber

Fiber adalah framework web yang terinspirasi oleh Express.js dari dunia Node.js, membuatnya sangat mudah diadopsi oleh developer yang sudah familiar dengan Express. Dibangun di atas Fasthttp, Fiber diklaim sebagai salah satu framework Go tercepat untuk membangun API.

# Library

## GORM

GORM (Go-ORM) adalah library ORM (Object-Relational Mapper) yang paling populer untuk Go. Tujuannya adalah untuk mempermudah interaksi dengan database SQL. Dengan GORM, Anda bisa bekerja dengan objek Go (structs) alih-alih menulis query SQL mentah, yang mempercepat pengembangan.

## sqlx

sqlx adalah ekstensi dari package database/sql bawaan Go. Ia menyediakan beberapa fitur tambahan yang sangat berguna, seperti memetakan hasil query database langsung ke struct Go tanpa perlu melakukan scan manual setiap kolom. sqlx adalah jalan tengah yang bagus antara menulis SQL mentah dan menggunakan ORM penuh.

## sqlc

sqlc adalah tool yang menghasilkan kode Go yang type-safe dari query SQL mentah yang Anda tulis. Anda menulis query di file .sql, dan sqlc akan membuatkan fungsi-fungsi Go yang sesuai. Ini memberikan performa SQL mentah dengan keamanan dan kemudahan yang mirip ORM.

# Driver

## MySQL

- go-sql-driver/mysql: Ini adalah driver paling umum dan stabil untuk menghubungkan aplikasi Go dengan database MySQL.

## PostgreSQL

- lib/pq: Driver yang sudah lama ada dan banyak digunakan untuk PostgreSQL.
- pgx: Driver yang lebih modern dan berkinerja tinggi untuk PostgreSQL. pgx seringkali direkomendasikan untuk proyek baru karena fitur dan performanya yang lebih baik.

## SQLite

- mattn/go-sqlite3: Driver yang paling populer untuk SQLite, yang memungkinkan Anda membuat database berbasis file yang ringan, cocok untuk aplikasi kecil atau testing.
