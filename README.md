# Capstone Project Modul 3 - Customer Churn E-Commerce Prediction

**Bussiness Context**


E-Commerce merupakan salah satu bentuk perkembangan teknologi dalam bidang ekonomi yang meliputi proses promosi, pembelian dan pemasaran produk melalui media elektronik atau internet. Di tengah perkembangan arus teknologi dan informasi digital yang semakin canggih. Aktivitas E-Commerce adalah suatu penerapan dari E-Business atau bisnis elektronik yang cukup efektif, sehingga platform eCommerce semakin banyak dan persaingan semakin ketat. 
Sebuah perusahaan eCommerce sebut saja **"Black E-Commerce"** menjalankan sebuah bisnis online retail dengan model B2C (Business to Consumer) dengan produk-produk yang ditawarkan seperti Laptop & Accesories, Mobile Phone, Fashion, Groceries, dan lainnya.  Perusahaan eCommerce saat ini berlomba-lomba berinovasi dalam menawarkan produk yang menarik kepada pelanggan. Bahkan, perusahaan saling mengakuisisi pelanggan antar perusahaan eCommerce satu sama lain. Sehingga pelanggan berhenti bertransaksi menggunakan platform perusahan eCommerce dan berpindah menggunakan platform eCommerce lainnya sangat mungkin terjadi. Perilaku pelanggan tersebut disebut dengan
istilah ***Churn***. Pelanggan adalah salah satu aset terpenting perusahaan dan memiliki peran yang sangat penting dalam meningkatkan daya saing pasar dan kinerja perusahaan. Melansir dari halaman web <a href="https://www.europeanbusinessreview.com/is-acquiring-new-customers-more-expensive-than-keeping-them/">Europian Business Review</a>, Penelitian menunjukkan bahwa biaya untuk mendapatkan pelanggan baru seringkali lebih tinggi (5 kali lebih mahal) daripada biaya mempertahankan pelanggan lama. Perusahaan akan mengalami kerugian yang cukup signifikan apabila terdapat pelanggan yang melakukan *Churn*.

**Problem Statement**

*Customer Churn* merupakan salah satu masalah yang harus dihadapi setiap bisnis eCommerce karena pada dasarnya pelanggan selalu datang dan pergi. Tetapi jika *Churn* dibiarkan, hal itu dapat berdampak besar pada pendapatan dalam jangka panjang. Karena pasar eCommerce tumbuh lebih kompetitif, selama bertahun-tahun menjalankan bisnis, biaya akuisisi pelanggan naik karena perlu menghabiskan lebih banyak untuk iklan digital dan pemasaran agar tetap terlihat. Jika perusahaan tidak dapat mempertahankan pelanggan setelah investasi awal, maka keuntungan akan menurun secara signifikan. Ditambah lagi jika ada pelanggan yang melakukan *Churn* karena kecewa, kemungkinan mereka akan bercerita kepada orang lain sehingga mempengaruhi orang lain untuk tidak menggunakan platform eCommerce perusahaan kita. 

**Goals**

Berdasarkan permasalahan tersebut, mengurangi *customer churn* merupakan tujuan bisnis utama perusahaan. Perusahaan ini ingin memiliki kemampuan untuk memprediksi kemungkinan pelanggan yang akan melakukan churn/tidak, serta mengetahui faktor/variabel apa yang dapat mempengaruhi pelanggan berhenti(churn)/tidak. Sehingga perusahaan dapat membuat perencanaan penawaran yang lebih sesuai kepada pelanggan yang berpotensi melakukan chun untuk mempertahankan pelanggan.

**Analytic Approach**

Jadi, yang perlu kita lakukan adalah menganalisis data untuk dapat menemukan pola dari fitur-fitur yang ada, yang membedakan pelanggan yang cenderung akan melakukan churn dan yang tidak. 

Selanjutnya, kita akan membangun suatu model klasifikasi yang akan membantu perusahaan untuk dapat menyediakan 'tool' prediksi pelanggan yang kemungkinan akan churn atau tidak.

**Evaluation Metrics**

- **Type I error (False Positive)** mengacu pada pelanggan yang diprediksi akan berhenti tetapi berencana untuk tetap loyal. <br> <br>
Konsekuensi : *Jika kita mengasumsikan eCommerce berinvestasi dalam mempertahankan pelanggan yang berisiko untuk churn, seperti menawarkan produk baru dengan harga spesial, meningkatkan jumlah cashback, dll,* **Maka adanya potensi biaya pengeluaran yang sia - sia untuk Tipe I error ini karena biaya investasi diberikan kepada pelanggan yang tidak berencana untuk Churn**

- **Type II error (False Negative)** mengacu pada pelanggan yang akan melakukan *Churn* tetapi diprediksi tetap loyal/tidak churn. <br> <br> 
*Konsekuensi : Dengan asumsi eCommerce hanya memfokuskan investasinya dalam mempertahankan pelanggan yang berisiko agar tidak Churn dan terus memberikan penawaran yang sama kepada pelanggan setia lain, sehingga ***Tipe II Error ini adalah kehilangan pelanggan***. Perusahaan akan sangat merugi karena biaya untuk mendapatkan pelanggan baru diperkirakan lebih tinggi dibandingkan dengan mempertahankan pelanggan saat ini.*

Berdasarkan konsekuensinya, maka sebisa mungkin yang akan kita lakukan adalah membuat model yang dapat **mengurangi jumlah kehilangan pelanggan** dari perusahaan tersebut, dan mengurangi biaya investasi yang sia-sia dalam mempertahankan pelanggan yang diprediksi akan *Churn* namun kenyataannya pelanggan tidak akan *Churn*. Jadi harus kita seimbangkan antara precision dan recallnya dari kelas positive (Customer churn). Jadi nanti metric yang akan kita gunakan adalah **roc_auc**, karena jika diperhatikan dataset yang dimiliki memiliki imbalanced data.
