# Konsep Dasar Go

Berikut adalah penjelasan untuk setiap konsep dasar yang penting dalam bahasa Go.

## 1. Variabel dan Tipe Data

Variabel adalah sebuah nama yang digunakan untuk menyimpan nilai. Di Go, setiap variabel memiliki tipe data yang spesifik dan tidak bisa diubah (statically typed).

Deklarasi Eksplisit: Menggunakan kata kunci var.

Deklarasi Singkat: Menggunakan := (hanya bisa di dalam fungsi).

Tipe Data Dasar:

string: Teks (diapit oleh ").

int: Bilangan bulat (contoh: 5, -10).

float64: Bilangan desimal (contoh: 3.14).

bool: Logika true atau false.

```go
// main.go
package main

import "fmt"

func main() {
// Deklarasi eksplisit dengan var
var nama string = "Budi"

    // Deklarasi singkat dengan :=
    umur := 25

    // Deklarasi tanpa nilai awal (akan diisi zero-value, untuk angka adalah 0)
    var tinggi float64

    isLulus := true

    fmt.Println("Nama:", nama)
    fmt.Println("Umur:", umur)
    fmt.Println("Tinggi:", tinggi)
    fmt.Println("Lulus:", isLulus)

}
```

## 2. Fungsi

Fungsi adalah blok kode yang dirancang untuk melakukan tugas tertentu. Fungsi membuat kode menjadi modular dan dapat digunakan kembali.

func: Kata kunci untuk mendefinisikan fungsi.

(parameter tipe): Input yang diterima oleh fungsi.

tipeReturn: Tipe data dari nilai yang dikembalikan.

```go
package main

import "fmt"

// Fungsi `tambah` menerima dua integer (a dan b)
// dan mengembalikan sebuah integer.
func tambah(a int, b int) int {
return a + b
}

func main() {
hasil := tambah(5, 3)
fmt.Println("Hasil penjumlahan:", hasil) // Output: 8
}
```

## 3. Control Flow

Control flow adalah urutan eksekusi kode. Go menggunakan if-else, for, dan switch untuk mengontrol alur program.

Uniknya Go: Go hanya memiliki satu jenis perulangan, yaitu for.

```go
package main

import "fmt"

func main() {
nilai := 85

    // Kondisi if-else
    if nilai > 90 {
        fmt.Println("Sangat Baik")
    } else if nilai > 75 {
        fmt.Println("Baik")
    } else {
        fmt.Println("Cukup")
    }

    // Perulangan for
    for i := 0; i < 3; i++ {
        fmt.Println("Angka:", i)
    }

}
```

## 4. Struktur Data

Struktur data digunakan untuk menyimpan dan mengelola kumpulan data. Yang paling umum di Go adalah Array, Slice, dan Map.

Array: Kumpulan data dengan ukuran yang tetap.

Slice: Kumpulan data yang dinamis dan fleksibel (dibangun di atas Array). Jauh lebih umum digunakan daripada Array.

Map: Kumpulan pasangan key-value.

```go
package main

import "fmt"

func main() {
// Slice (ukuran dinamis)
buah := []string{"Apel", "Jeruk", "Mangga"}
buah = append(buah, "Anggur") // Menambah elemen baru
fmt.Println("Buah-buahan:", buah)

    // Map (key: string, value: int)
    hargaBuah := map[string]int{
        "Apel":  5000,
        "Jeruk": 4000,
    }
    fmt.Println("Harga Apel:", hargaBuah["Apel"])

}
```

## 5. Pointer

Pointer adalah variabel yang menyimpan alamat memori dari variabel lain. Ini memungkinkan Anda untuk mengubah nilai variabel secara tidak langsung.

&: Operator "address of", untuk mendapatkan alamat memori suatu variabel.

\*: Operator "dereference", untuk mengakses nilai yang ada di sebuah alamat memori.

```go
package main

import "fmt"

// Fungsi ini menerima pointer ke integer
func ubahNilai(angka *int) {
*angka = 100 // Mengubah nilai di alamat memori tersebut
}

func main() {
x := 10
fmt.Println("Nilai awal x:", x)

    ubahNilai(&x) // Mengirim alamat memori dari x ke fungsi

    fmt.Println("Nilai akhir x:", x) // Output: 100

}
```

## 6. Error Handling

Go memiliki pendekatan unik untuk menangani error. Fungsi yang berpotensi gagal akan mengembalikan dua nilai: hasil dan error. Error akan bernilai nil jika tidak ada masalah.

Ini memaksa programmer untuk secara eksplisit memeriksa kemungkinan error.

```go
package main

import (
"fmt"
"strconv"
)

func main() {
// Mencoba mengubah string "123" menjadi integer
angka, err := strconv.Atoi("123")
if err != nil {
// Blok ini tidak akan dieksekusi karena "123" valid
fmt.Println("Terjadi error:", err)
} else {
fmt.Println("Angka berhasil diubah:", angka)
}

    // Mencoba mengubah string "abc" yang tidak valid
    angka2, err2 := strconv.Atoi("abc")
    if err2 != nil {
        // Blok ini akan dieksekusi
        fmt.Println("Terjadi error:", err2)
    } else {
        fmt.Println("Angka berhasil diubah:", angka2)
    }

}
```
