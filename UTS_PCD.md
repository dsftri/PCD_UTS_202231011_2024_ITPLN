
Penjelasan UTS Praktikum

1. mendeteksi warna pada citra

a. Tahapan mendeteksi warna pada citra:
- Histogram merah menunjukkan bahwa intensitas piksel merah paling banyak terkonsentrasi di sekitar nilai 100-150.
- Histogram hijau menunjukkan intensitas piksel hijau yang cukup merata dengan sedikit puncak di sekitar nilai 100.
- Histogram biru menunjukkan intensitas piksel biru yang juga merata dengan sedikit puncak di sekitar nilai 100.
- Histogram warna gabungan menunjukkan kombinasi intensitas piksel dari semua saluran warna, dengan distribusi yang merata namun dengan beberapa puncak yang menunjukkan kemungkinan warna dominan dalam gambar.
Penjelasan Tahapan:

Deteksi warna pada citra merupakan proses di mana kita mengidentifikasi dan memisahkan wilayah-wilayah dengan warna tertentu dari citra digital. Proses ini melibatkan konversi citra ke ruang warna tertentu, seperti HSV (Hue, Saturation, Value), yang memungkinkan kita untuk dengan mudah menentukan batas-batas warna yang ingin dideteksi. Dalam implementasi yang disajikan, penggunaan ruang warna HSV memungkinkan deteksi warna yang lebih akurat karena memisahkan informasi warna dari informasi kecerahan dan saturasi.

Pertama, kita konversi citra asli ke ruang warna HSV untuk mempermudah proses deteksi warna. Kemudian, kita tentukan rentang warna yang ingin dideteksi dalam ruang warna tersebut, misalnya, untuk warna biru, merah, dan hijau. Rentang warna ini direpresentasikan oleh batas atas dan batas bawah dalam komponen warna hue (H). Kita lakukan ini karena ruang warna HSV memiliki komponen H yang mewakili warna secara langsung.

Setelah itu, kita buat masker untuk setiap rentang warna yang telah ditentukan. Masker ini berisi piksel-piksel yang sesuai dengan rentang warna yang ingin dideteksi. Dengan menggunakan operasi bitwise OR, kita dapat menggabungkan masker-masker tersebut untuk mendeteksi semua warna yang diinginkan dalam satu citra.

Hasil akhir dari proses deteksi warna adalah citra biner di mana piksel-piksel yang sesuai dengan warna yang ingin dideteksi memiliki nilai 1 (putih), sedangkan piksel-piksel lain memiliki nilai 0 (hitam). Citra biner ini dapat digunakan untuk berbagai tujuan, seperti segmentasi objek berwarna dalam sebuah citra atau mengambil tindakan berdasarkan deteksi warna, seperti pengenalan objek atau navigasi robot.

Dengan menggunakan deteksi warna, kita dapat mengidentifikasi dan mengisolasi objek-objek berwarna tertentu dalam citra, yang berguna dalam berbagai aplikasi seperti visi komputer, penginderaan jarak jauh, dan robotika. Namun, perlu diingat bahwa keberhasilan deteksi warna sangat tergantung pada kualitas citra, pencahayaan, dan kecocokan rentang warna yang telah ditentukan. Oleh karena itu, penting untuk melakukan kalibrasi dan pengujian yang tepat untuk memastikan akurasi deteksi warna yang diinginkan dalam suatu aplikasi.

2. Menganalisis Histogram

- Histogram adalah representasi visual dari distribusi frekuensi intensitas piksel dalam sebuah citra. Histogram menunjukkan seberapa sering setiap tingkat intensitas piksel muncul dalam citra. Dalam konteks analisis histogram, kita dapat memahami karakteristik citra secara lebih mendalam, termasuk informasi tentang kontras, kecerahan, dan distribusi warna.

- Dalam implementasi yang disajikan, histogram dibuat untuk citra asli serta untuk setiap saluran warna (merah, hijau, dan biru) secara terpisah. Ini memungkinkan kita untuk melihat distribusi intensitas piksel pada masing-masing saluran warna, yang memberikan wawasan tentang seberapa banyak warna tertentu yang dominan dalam citra. Misalnya, histogram merah yang tinggi menunjukkan keberadaan banyak piksel dengan intensitas merah yang tinggi.

- Dari histogram citra asli, kita dapat mengevaluasi tingkat kontras dan distribusi kecerahan secara keseluruhan. Jika histogram menunjukkan konsentrasi piksel pada ujung spektrum intensitas, citra tersebut mungkin memiliki kontras yang tinggi. Sebaliknya, jika histogram menyebar secara merata di sepanjang rentang intensitas, citra mungkin memiliki kontras yang rendah.

- Analisis histogram juga memberikan wawasan tentang kecenderungan warna dalam citra. Misalnya, jika histogram saluran hijau memiliki puncak yang lebih tinggi daripada histogram saluran lainnya, ini menandakan dominasi warna hijau dalam citra. Dengan memahami histogram, kita dapat mengidentifikasi pola, tekstur, dan karakteristik visual lainnya dalam citra, yang dapat digunakan untuk keperluan pemrosesan lebih lanjut, seperti segmentasi objek atau penyesuaian warna.

3. Penjelasan Ambang Batas 

- Mencari dan mengurutkan ambang batas terkecil sampai dengan terbesar. 
A. Deteksi Warna Biru (Blue)
- Nilai ambang batas bawah : [100, 50, 50]
- Nilai ambang batas atas : [130, 255, 255]
B. Deteksi Warna Merah-Biru
> Merah
- Nilai ambang batas bawah: [0, 50, 50]
- Nilai ambang batas atas: [10, 255, 255]
- Nilai ambang batas tambahan bawah : [170, 50, 50]
- Nilai ambang batas tambahan atas : [180, 255, 255]
> Biru
- Nilai ambang batas bawah : [100, 50, 50]
- Nilai ambang batas atas: [130, 255, 255]
C. Deteksi Warna Merah-Hijau-biru

Merah
- Nilai ambang batas bawah: [0, 50, 50]
- Nilai ambang batas atas: [10, 255, 255]
- Nilai ambang batas tambahan bawah : [170, 50, 50]
- Nilai ambang batas tambahan atas : [180, 255, 255]
Hijau
- Nilai ambang batas bawah : [35, 50, 50]
- Nilai ambang batas atas : [80, 255, 255]
Biru
- Nilai ambang batas bawah : [100, 50, 50]
- Nilai ambang batas atas: [130, 255, 255]
 
Nilai-nilai ambang batas dipilih berdasarkan analisis terhadap sifat-sifat warna dalam ruang warna HSV serta tujuan spesifik dari deteksi warna yang dilakukan. Rentang nilai Hue dipilih dalam skala 0-180 dalam OpenCV karena Hue merepresentasikan warna dalam rentang 0-360 derajat, dengan warna merah yang mendekati nilai 0 atau nilai 180 karena sifat siklik dari spektrum warna. Rentang ambang batas yang dipilih memperhitungkan distribusi warna utama seperti merah, hijau, dan biru dalam rentang Hue yang relevan dengan nilai-nilai ambang batas sekitar 0-180.

Sementara itu, nilai-nilai ambang batas untuk Saturation (S) dan Value (V) dipilih untuk mempengaruhi deteksi warna berdasarkan tingkat saturasi (kejenuhan) dan nilai kecerahan warna. Rentang yang luas dipilih untuk S dan V untuk memberikan fleksibilitas dalam menangkap variasi dalam gambar, yang dapat mencakup perubahan dalam kondisi cahaya atau karakteristik gambar. Namun, penting untuk dicatat bahwa pemilihan nilai-nilai ambang batas ini dapat disesuaikan berdasarkan kondisi khusus dari citra yang sedang diproses, serta preferensi atau kebutuhan pengguna dalam deteksi warna.

Tahapan menyelesaikan projek:

1. Membaca Gambar
bertujuan untuk membaca sebuah gambar dengan nama file 'UTSPRAKB.jpg' menggunakan fungsi imread dari modul img (yang diduga sebagai alias dari matplotlib.image). Gambar yang dibaca kemudian ditampilkan menggunakan fungsi imshow dari modul plt (yang diduga sebagai alias dari matplotlib.pyplot), sehingga kita dapat melihat visualisasi dari gambar tersebut.
2. Deteksi Warna Pada Citra
bertujuan untuk membagi gambar menjadi tiga saluran warna (merah, hijau, biru) dan menampilkan setiap saluran warna secara terpisah bersamaan dengan gambar asli dalam satu gambar subplot. Ini memungkinkan kita untuk melihat kontribusi masing-masing saluran warna terhadap citra asli.
3. Membuat Histogram dan Membuat Fungsi untuk Meningkatkan Brightness dan Mendeteksi Warna
Tahap 3 dalam proses ini melibatkan pembuatan fungsi-fungsi yang akan digunakan untuk meningkatkan kecerahan gambar serta mendeteksi warna tertentu di dalamnya.

Untuk meningkatkan kecerahan gambar, fungsi increase_brightness akan dibuat. Fungsi ini akan melakukan konversi warna dari BGR ke HSV, lalu meningkatkan nilai kecerahan pada saluran Value (V) dalam ruang warna HSV, dan akhirnya mengembalikan gambar dalam format BGR.

Selanjutnya, untuk mendeteksi warna tertentu, fungsi-fungsi seperti detect_and_highlight_blue, detect_and_highlight_red_blue, dan detect_and_highlight_red_green_blue akan dibuat. Setiap fungsi ini akan melakukan konversi warna dari BGR ke HSV, lalu menerapkan mask untuk mendeteksi warna yang spesifik (misalnya, biru, merah-biru, atau merah-hijau-biru) dan mengembalikan gambar yang sudah diproses dengan penekanan warna tersebut.
4. Menampilkan Hasil
Menampilkan Hasil, hasil dari masing-masing fungsi diterapkan pada gambar ditampilkan menggunakan fungsi imshow dari matplotlib. Hasil ini menampilkan gambar yang telah ditingkatkan brightness dan ditekan warna.

TEORI YANG MENDUKUNG PROJEK

Proyek ini melibatkan beberapa konsep dasar dalam pengolahan citra dan penggunaan ruang warna HSV untuk deteksi warna. Berikut adalah beberapa teori yang mendukung proyek ini:

1. Konversi Warna: Konsep dasar dalam pengolahan citra adalah konversi warna. Dalam proyek ini, terjadi konversi warna dari ruang warna BGR (Blue, Green, Red) ke HSV (Hue, Saturation, Value). Ruang warna HSV lebih intuitif dalam mendeskripsikan warna karena memisahkan informasi tentang warna, kejenuhan, dan kecerahan.

2. Histogram: Histogram digunakan untuk menganalisis distribusi intensitas warna dalam gambar. Pada tahap pembuatan histogram dalam proyek ini, histogram digunakan untuk menganalisis distribusi intensitas warna dalam gambar asli serta dalam setiap saluran warna (merah, hijau, biru) secara terpisah.

3. Deteksi Warna: Deteksi warna dilakukan dengan membuat mask untuk menangkap piksel berdasarkan rentang nilai HSV yang mewakili warna yang ingin dideteksi. Pada proyek ini, dilakukan deteksi warna biru, merah-biru, dan merah-hijau-biru. Ini dilakukan dengan membuat mask untuk setiap warna (biru, merah, hijau) dan menggabungkan mask tersebut untuk mendapatkan area yang menyoroti warna tertentu.

4. Operasi Bitwise: Dalam pengolahan citra, operasi bitwise digunakan untuk melakukan operasi logika pada piksel gambar. Pada proyek ini, operasi bitwise digunakan untuk menggabungkan masker warna yang telah dibuat untuk mendeteksi warna biru, merah, dan hijau.

5. Penyisipan Gambar: Pada akhirnya, hasil deteksi warna ditampilkan dengan menyisipkan area yang dideteksi (warna hitam) ke dalam gambar asli. Ini memberikan visualisasi yang jelas tentang di mana warna-warna yang diinginkan terdapat dalam gambar.


