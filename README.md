# UTS Graf Sains Data: Neo4j, Python Driver, dan Rekomendasi

**Nama:** Arimbi Deby Setyoningrum
**NIM:** 24-31554186
**Mata kuliah:** Graf Sains Data

## Ringkasan
Proyek ini mengimpor data interaksi e-commerce RetailRocket ke database graf Neo4j, membuat proyeksi graf (User-Item dan Item-Item), menghitung similarity, lalu membuat rekomendasi item dengan KNN berbasis item.

**Periode yang dipilih (kombinasi no. 18):**
- P1 (training): 01-15 Juni 2015
- P2 (testing): 16-31 Juli 2015

## Isi repositori
`UTS2.ipynb:`  Notebook utama (kode, output, dan penjelasan tiap soal) 
`events_p1.csv:` Data interaksi periode P1 (300.563 baris), dimasukkan ke Neo4j 
`events_p2.csv:` Data interaksi periode P2 (364.206 baris), dipakai sebagai kunci jawaban evaluasi 

## Sumber data
RetailRocket E-commerce Dataset (Roman Zykov), Kaggle:
https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset

`events_p1.csv` dan `events_p2.csv` adalah hasil filter `events.csv` berdasarkan timestamp. File `events.csv` asli (±94 MB) tidak diunggah karena ukurannya besar. Untuk menjalankan ulang dari awal, unduh `events.csv` dari Kaggle dan taruh satu folder dengan notebook.

## Hasil utama
- Graf P1: 160.017 simpul Visitor, 79.896 simpul Item, 300.563 relasi (VIEWED, ADDED_TO_CART, BOUGHT).
- Matriks User-Item berukuran 160.017 × 79.896, sangat sparse (density 0,0018%).
- Proyeksi Item-Item dipilih karena lebih efisien dan efektif dibanding User-User.
- Similarity (cosine) item acuan 5411 disimpan ke graf sebagai relasi `SIMILAR_TO`.
- Evaluasi KNN item-based (k = 5) pada 200 user acak: Hit@5 = 0,020 dan NDCG@5 = 0,0040.

## Cara menjalankan
1. Pasang dan jalankan Neo4j (Desktop atau Server) di `neo4j://127.0.0.1:7687`.
2. Buat virtual environment dan pasang paket: neo4j, pandas, numpy, scipy, scikit-learn, networkx, matplotlib, tqdm.
3. Ubah `PASSWORD` di notebook sesuai password Neo4j kamu (di repo ini diisi `"password"`).
4. Jalankan `UTS2.ipynb` dari atas ke bawah (Restart & Run All).

Versi yang dipakai: Python (versi), neo4j driver (versi dari `pip show neo4j`), Neo4j (versi).
