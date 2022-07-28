# E-Commerce Customer Churn Prediction
Capstone Project modul 3 ini bertujuan untuk mengimplementasikan materi yang telah dipelajari terkait modul machine learning dalam sebuah proyek. 

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

**Data Understanding**
Note :
- Dataset ini hanyalah data *training* yang digunakan untuk membangun model dan akan diusahakan agar model memiliki skor evaluation metrics setinggi mungkin. 
- Setiap baris data mempresentasikan informasi riwayat transaksi seorang pelanggan di masa lalu

### Attibute Information

| Attribute | Data Type, Length | Description |
| --- | --- | --- |
| Tenure | Float | Tenure of customer in ecommerce company |
| WarehouseToHome | Float | Distance in between warehouse to home of customer |
| NumberOfDeviceRegistered | Integer | Total number of devices is registered on particular customer |
| PreferedOrderCat | Text | Preferred order category of customer in last month |
| SatisfactionScore | Integer | Satisfactory score of customer on service |
| MaritalStatus | Text | Marital status of customer |
| NumberOfAddress | Integer | Total number of added added on particular customer |
| Complain | Integer | Any complaint has been raised in last month |
| DaySinceLastOrder | Float | Day Since last order by customer |
| CashbackAmount | Float | Average cashback in last month |
| Churn | Integer | 0 - Not Churn, 1 - Churn|

**Data Analyze**

![newplot](https://user-images.githubusercontent.com/73053128/170018922-7f6e4d89-46b4-4089-96a5-e99589a37ec2.png)
***
**Observation :**

Dapat dilihat berdasarkan hasil di atas, data yang dimiliki cukup `imbalance`. Dimana hanya 17.1% data kelas positif (Churn). Hal ini akan mempengaruhi hasil klasifikasi nantinya, maka dari itu akan dilakukan pendekatan untuk mengatasi masalah data imbalance ini dengan metode resampling menggunakan SMOTE (Synthetic Minority Oversampling) yaitu teknik yang dapat membangkitkan sejumlah data baru yang mirip dengan data kelas minoritas hingga distribusinya lebih berimbang.

***

# Model Building & Evaluation

Sebelum membangun model, beberapa tahapan data cleaning yang telah dilakukan adalah melakukan penanganan terhadap missing value karena ditemukan missing value dengan tipe Missing Not At Random dimana, beberapa variabel mengandung missing value ketika nilai variable `CashbackAmount`nya berada dalam range tertentu maka ditambahkan  suatu variabel binary missing value flags dan melakukan impute missing value dengan nilai median, kemudian dilakukan juga pengecekan dan pengananan terhadap outliers, melakukan log transform untuk variabel `WarehouseToHome` karena memiliki nilai right skewness yang cukup tinggi dibandingkn dengan variabel lainnya, mengubah kategori beberapa fitur/kolom, melakukan binning data, encoding, mengubah tipe data dan urutan kolom/fitur.

Untuk membangun model ini dilakukan Handling Imbalanced Data dengan SMOTENC, dapat dilihat pada bagian 'Modelling' notebook. Adapun model yang digunakan dalam project ini adalah beberapa model untuk mendapat model dengan evaluation metrics terbaik. 
| Models | ROC_AUC | Accuracy | F1-Score | Precision | Recall|
|---|---|---|---|---|---|
|RandomForestClassifier|	0.960534|	0.929624|	0.804334|	0.766112|	0.848442|
|XGBClassifier|	0.955499|	0.927331|	0.799374|	0.759855	|0.845544|
|VotingClassifier|	0.935575|	0.892775|	0.729127|	0.642475|	0.843942|
|GradientBoostingClassifier|	0.912976|	0.864068|	0.670206|	0.573413|	0.806936|
|SVC|	0.898197|	0.824187|	0.612209|	0.492370| 0.809855|
|AdaBoostClassifier|	0.895630|	0.832821|	0.623445|	0.507646|	0.808428|
|KNeighborsClassifier|	0.885663|	0.823425|	0.605713|	0.490389|	0.793591|
|LogisticRegression|	0.877712|	0.796237|	0.578303|	0.448242|	0.815891|
|DecisionTreeClassifier|	0.856163|	0.897352|	0.725279|	0.669817|	0.793569|

Kemudian dilakukan perbandingan anatara hasil klasifikasi Random Forest dan XGBoost dengan menggunakan Hyperparameter Tunning terbaik dari hasil Grid Serach CV, sehingga diperoleh peningkatan evaluation metricsnya sebagai berikut:
| Models | ROC_AUC | Accuracy | F1-Score | Precision | Recall|
|---|---|---|---|---|---|
|XGBClassifier|	0.963718|	0.935717|	0.820812|	0.785042|	0.861809|
|RandomForestClassifier|	0.961793|	0.932925|	0.815053|	0.770060|	0.867713|

Berdasarkan hasil evaluation metrics tersbeut, maka **Best Model yang dipilih adalah Model XGBoost** yang telah dilakukan Tuning.

Adapun perbandingan ROC Curve XGBoost default dan setelah Tuning sebagai berikut.

![Screenshot (128)](https://user-images.githubusercontent.com/73053128/170023240-5e883e24-072a-400d-a507-bf0b3768acd8.png)

XGBoostClassifier setelah dituning hyperparameternya mendapatkan nilai ROC AUC yang lebih baik dimana awalnya 0.89 menjadi 0.91.


***
Note : Terdapat file 'Load Model and Testing dataset.ipynb', bisa digunakan untuk load model dan menguji dataset test untuk diprediksi menggunakan model yang telah kita buat.

# Thank you for reading until the end!
### Nila Wildanul Husna
