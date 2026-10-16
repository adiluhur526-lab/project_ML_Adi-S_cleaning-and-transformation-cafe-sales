# Data Cleaning dan Transformation: Cafe Sales

Project latihan membersihkan dan mengubah dataset transaksi kafe yang sengaja dibuat "kotor", menggunakan Python dan pandas.

- **Nama:** Adi Luhur Kurniawan Siregar
- **NIM / Kelas:** 241011401107 / 05TPLE014
- **Mata kuliah:** Machine Learning

## Dataset
Cafe Sales – Dirty Data for Cleaning Training (Kaggle):
https://www.kaggle.com/datasets/ahmedmohamed2003/cafe-sales-dirty-data-for-cleaning-training

Kolom: `Transaction ID`, `Item`, `Quantity`, `Price Per Unit`, `Total Spent`, `Payment Method`, `Location`, `Transaction Date`.

## Pertanyaan analisis
Menu apa yang menghasilkan pendapatan terbesar, dan bagaimana kualitas data (data kosong, `ERROR`, `UNKNOWN`) memengaruhi hasil analisisnya?

## Struktur folder
```
project-folder/
├── clean/
│   ├── dirty_cafe_sales_clean.csv
│   └── dirty_cafe_sales_transformed.csv
├── cleaning.ipynb
├── dirty_cafe_sales.csv
├── requirements.txt
└── README.md
```

## Cara menjalankan
```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```
Letakkan `dirty_cafe_sales.csv` satu folder dengan `cleaning.ipynb`, buka `cleaning.ipynb` di VS Code, pilih kernel `venv`, lalu **Run All**. Hasil akan tersimpan di folder `clean/`.

## Tahapan
**Data cleaning**
1. Mengenali masalah: data kosong, nilai `ERROR`/`UNKNOWN`, tipe data salah, duplikat.
2. Menyeragamkan nama kolom dan merapikan teks.
3. Mengganti `ERROR`/`UNKNOWN` menjadi data kosong.
4. Memperbaiki tipe data (angka dan tanggal).
5. Menghapus duplikat.
6. Melengkapi data kosong dengan aturan logis (`total_spent = quantity × price_per_unit`, harga tetap per menu).
7. Mengisi kategori kosong dengan `Tidak Diketahui` dan menghapus baris yang data intinya tidak dapat dipulihkan.
8. Validasi hasil.

**Data transformation**
1. Fitur tanggal (tahun, bulan, nama hari, akhir pekan).
2. Binning total belanja (Rendah / Sedang / Tinggi).
3. Scaling (min-max dan z-score).
4. One-Hot Encoding.
5. Agregasi per menu dan lokasi.

## Hasil
| | Sebelum | Sesudah |
|---|---|---|
| Jumlah baris | 10.000 | 9.514 |
| Jumlah kolom | 8 | 15 |
| Sel kosong / ERROR / UNKNOWN | 10.082 | 0 |

- Duplikat yang ditemukan: 0.
- Baris dihapus karena data inti (jumlah, harga, total, tanggal) tidak dapat dipulihkan: 486.

Menu terlaris: **Salad** dengan total pendapatan 18.220 (1.214 transaksi), diikuti Sandwich (13.068) dan Smoothie (12.776).

Catatan: sekitar 40% data `location` dan 32% data `payment_method` tidak diketahui (`Tidak Diketahui`), sehingga analisis per lokasi dan metode pembayaran kurang akurat.

File hasil: `clean/dirty_cafe_sales_clean.csv` dan `clean/dirty_cafe_sales_transformed.csv`.
