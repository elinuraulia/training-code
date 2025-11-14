🧾 Mesin Kasir Sederhana

Project Latihan Pemrograman Dasar (Berbasis Function)

# 📌 Gambaran Umum

Project ini adalah latihan sederhana untuk memahami cara kerja function dalam pemrograman. Studi kasus yang dipakai adalah mesin kasir, di mana program akan melakukan beberapa tugas dasar seperti menghitung total belanja, menghitung diskon, dan membuat struk sederhana.

Project ini sengaja dibuat simpel, supaya fokus kamu tetap ke hal-hal fundamental: bagaimana memecah masalah menjadi beberapa fungsi kecil yang rapi dan mudah dipahami.


# 🎯 Tujuan Pembelajaran

Lewat project kecil ini, kamu akan belajar untuk:

- Memahami cara menyusun function yang terpisah tapi saling bekerja sama
- Membuat alur program yang terstruktur
- Melatih logika pemrograman menggunakan kasus dunia nyata
- Membiasakan diri membangun project dari konsep terlebih dahulu 


# 🧩 Fitur yang Akan Dibuat

Fokusnya cuma fitur dasar yang bisa dicapai oleh pemula:

1. Menampilkan daftar barang
2. Memilih barang dan jumlah yang ingin dibeli
3. Menghitung total harga
4. Menghitung diskon sederhana (opsional)
5. Membuat ringkasan belanja (struk singkat)

Semua fitur ini nantinya dibuat menggunakan beberapa function terpisah agar alurnya bersih


# 🛠 Konsep Function yang Digunakan

Project ini melatih konsep dasar seperti:

-Function tanpa parameter
-Function dengan parameter
-Function yang mengembalikan nilai (return)
-Pemecahan program jadi beberapa fungsi kecil (modular)


# 📚 Alur Program (High Level)

1. Program menampilkan daftar barang
2. User memilih barang yang ingin dibeli
3. Program meminta jumlah barang
4. Function menghitung total
5. Function lain menghitung diskon (jika ada)
6. Program menampilkan ringkasan akhir / struk


# 📝 Catatan

Project ini hanya dibuat sebagai latihan mahasiswa pemula yang baru mempelajari Python sampai function. Semua logika dibuat sesederhana mungkin agar fokus belajar tidak melebar.

# Daftar barang dan harga
products = {
    "1": {"name": "Buku", "price": 10000},
    "2": {"name": "Pensil", "price": 2000},
    "3": {"name": "Penghapus", "price": 1500},
    "4": {"name": "Pulpen", "price": 3000}
}

# Function untuk menampilkan daftar barang
def show_products():
    print("\nDaftar Barang:")
    for code, item in products.items():
        print(f"{code}. {item['name']} - Rp{item['price']}")

# Function untuk memilih barang
def choose_product():
    while True:
        choice = input("Masukkan kode barang yang ingin dibeli: ")
        if choice in products:
            return choice
        else:
            print("Kode barang tidak valid. Coba lagi.")

# Function untuk memasukkan jumlah barang
def get_quantity():
    while True:
        try:
            qty = int(input("Masukkan jumlah barang: "))
            if qty > 0:
                return qty
            else:
                print("Jumlah harus lebih dari 0.")
        except ValueError:
            print("Masukkan angka yang valid.")

# Function untuk menghitung total harga
def calculate_total(cart):
    total = 0
    for item in cart:
        total += item["price"] * item["quantity"]
    return total

# Function untuk menghitung diskon (opsional)
def calculate_discount(total):
    if total >= 50000:  # diskon 10% untuk total >= 50.000
        return total * 0.1
    return 0

# Function untuk menampilkan struk
def print_receipt(cart, total, discount):
    print("\n--- STRUK BELANJA ---")
    for item in cart:
        print(f"{item['name']} x{item['quantity']} = Rp{item['price']*item['quantity']}")
    print(f"Total: Rp{total}")
    if discount > 0:
        print(f"Diskon: Rp{int(discount)}")
        print(f"Total Bayar: Rp{int(total - discount)}")
    print("---------------------")

# Main program
def main():
    cart = []
    while True:
        show_products()
        code = choose_product()
        quantity = get_quantity()

        cart.append({
            "name": products[code]["name"],
            "price": products[code]["price"],
            "quantity": quantity
        })

        more = input("Mau beli barang lain? (y/n): ").lower()
        if more != 'y':
            break

    total = calculate_total(cart)
    discount = calculate_discount(total)
    print_receipt(cart, total, discount)

# Jalankan program
if _name_ == "_main_":
    main()
