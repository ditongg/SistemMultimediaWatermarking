# Watermarking - Sinyal & Multimedia

**M.B. Adyanti Narandita | 18224026**

Implementasi digital watermarking pada gambar grayscale menggunakan metode LSB (Least Significant Bit), dilengkapi visualisasi DCT dan analisis ketahanan watermark terhadap kompresi JPEG.

---

## Deskripsi

Project ini mengeksplorasi dua konsep utama:

1. **LSB Watermarking** : menyisipkan watermark biner 64x64 ke bit paling rendah dari pixel gambar, sehingga perubahan tidak terlihat secara visual (perbedaan maksimal 1 nilai pixel).
2. **Analisis Ketahanan terhadap JPEG** : mengukur seberapa tahan watermark setelah gambar dikompresi dengan berbagai Quality Factor (QF=10 hingga QF=100) menggunakan Bit Error Rate (BER).

DCT (Discrete Cosine Transform) diimplementasikan secara manual tanpa library eksternal seperti `scipy`, menggunakan rumus matematis langsung dengan NumPy.

---

## Struktur Notebook

| Cell | Deskripsi |
|------|-----------|
| Cell 1 | Import library |
| Cell 2 | Load gambar dan konversi ke grayscale |
| Cell 3 | Buat watermark biner acak 64x64 |
| Cell 4 | Embed watermark dengan metode LSB |
| Cell 5 | Implementasi DCT manual + visualisasi quantization |
| Cell 6 | Kompresi JPEG dengan berbagai Quality Factor |
| Cell 7 | Ekstraksi watermark dan perhitungan BER |
| Cell 8 | Grafik BER vs Quality Factor |
| Cell 9 | Download semua hasil |

---

## Cara Penggunaan

1. Buka file `Tugas watermarking_18224026.ipynb` di [Google Colab](https://colab.research.google.com/)
2. Jalankan cell secara berurutan dari atas
3. Pada Cell 2, upload gambar ketika diminta (format JPG/PNG)
4. Hasil visualisasi dan grafik akan otomatis tersimpan dan bisa didownload di Cell 9

---

## Library yang Digunakan

- `numpy` — operasi array dan perhitungan matriks
- `Pillow` — baca dan simpan gambar
- `matplotlib` — visualisasi dan plotting
- `os` — operasi file

---

## Hasil

Watermark hanya bisa diekstrak kembali dengan BER < 0.1 pada **QF=100** (tanpa kompresi lossy signifikan). Pada QF di bawah 100, proses quantization JPEG merusak bit LSB sehingga watermark tidak dapat dipulihkan.

| Quality Factor | BER | Status |
|:-:|:-:|:-:|
| 10 | ~0.499 | Tidak bisa diekstrak |
| 50 | ~0.501 | Tidak bisa diekstrak |
| 90 | ~0.440 | Tidak bisa diekstrak |
| 100 | ~0.058 | Bisa diekstrak |
