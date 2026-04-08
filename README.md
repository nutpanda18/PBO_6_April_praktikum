class Karyawan:
    def __init__(self, nik, nama, jabatan):
        self.nik = nik
        self.nama = nama
        self.jabatan = jabatan

    def __str__(self):
        return f"{self.nik}\t{self.nama}\t{self.jabatan}"

class SistemKaryawan:
    def __init__(self):
        self.database = []

    def tambah_karyawan(self, karyawan):

        for k in self.database:
            if k.nik == karyawan.nik:
                print("❌ NIK sudah terdaftar!")
                return
        self.database.append(karyawan)
        print("✅ Karyawan berhasil ditambahkan!")

    def cari_karyawan(self, nik):
        for k in self.database:
            if k.nik == nik:
                print("\nData ditemukan:")
                print("NIK\tNama\tJabatan")
                print(k)
                return
        print("❌ Karyawan tidak ditemukan!")

    def tampilkan_semua(self):
        if not self.database:
            print("⚠️ Data karyawan masih kosong.")
            return
        print("\nDaftar Karyawan:")
        print("NIK\tNama\tJabatan")
        print("-" * 30)
        for k in self.database:
            print(k)



def main():
    sistem = SistemKaryawan()

    while True:
        print("\n=== SISTEM MANAJEMEN KARYAWAN ===")
        print("1. Tambah Karyawan")
        print("2. Cari Karyawan (NIK)")
        print("3. Lihat Semua")
        print("4. Keluar")

        pilihan = input("Pilihan: ")

        if pilihan == "1":
            nik = input("Masukkan NIK: ")
            nama = input("Masukkan Nama: ")
            jabatan = input("Masukkan Jabatan: ")

            karyawan = Karyawan(nik, nama, jabatan)
            sistem.tambah_karyawan(karyawan)

        elif pilihan == "2":
            nik = input("Masukkan NIK yang dicari: ")
            sistem.cari_karyawan(nik)

        elif pilihan == "3":
            sistem.tampilkan_semua()

        elif pilihan == "4":
            print("Terima kasih!")
            break

        else:
            print("❌ Pilihan tidak valid!")


main()
