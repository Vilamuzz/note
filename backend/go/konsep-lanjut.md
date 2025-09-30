# Konsep Lanjut Go

## 1. Goroutine

Goroutine adalah sebuah fungsi yang berjalan secara independen dan bersamaan dengan fungsi lainnya. Anggap saja seperti thread, tetapi jauh lebih ringan dan dikelola oleh Go runtime, bukan oleh sistem operasi.

Membuat goroutine sangatlah mudah, cukup tambahkan kata kunci go sebelum memanggil sebuah fungsi.

## 2. Channels

Channels adalah pipa komunikasi yang aman untuk mengirim dan menerima data antar goroutine. Ini mencegah kondisi balapan (race condition) di mana beberapa goroutine mencoba mengakses data yang sama secara bersamaan.

Contoh:

```go
package main

import (
    "fmt"
    "time"
)

// Fungsi ini akan berjalan di goroutine terpisah
func hitung(channel chan string) {
    fmt.Println("Mulai menghitung...")
    time.Sleep(2 * time.Second) // Simulasi pekerjaan berat

    // Kirim hasil ke channel setelah selesai
    channel <- "Perhitungan selesai!"
}

func main() {
    // Membuat sebuah channel string
    pesanChannel := make(chan string)

    // Memulai goroutine baru untuk menjalankan fungsi hitung
    go hitung(pesanChannel)

    fmt.Println("Menunggu hasil dari goroutine...")

    // Program akan berhenti (blocking) di sini sampai
    // ada data yang masuk ke channel.
    hasil := <-pesanChannel

    fmt.Println(hasil)
}
```
