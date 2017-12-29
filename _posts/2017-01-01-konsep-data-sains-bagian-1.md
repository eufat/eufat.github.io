Post pertama yeay.

Disini akan dibahas tentang konsep-konsep secara saintifik dan non-teknikal dari data sains. Di rangkaian post ini adalah ringkasan saya dari membaca berbagai buku tentang data sains yang ada di Evernote. Kenapa membahas data sains? karena menurut saya data sains adalah salah satu masa depan sains dan computer science. Sains disini yang saya maksud adalah sains murni seperti matematika, statistik dan fisika. Data sains sangat berhubungan erat dengan salah satu-term yang kita sering dengar, big data. Jika di analogikan big data itu seperti minyak mentah, sedangkan data sains itu sebagai metode cara memproses minyak itu supaya bisa di konsumsi.

Data di data sains terbagi menjadi 5 tipe yaitu,

1. Structured (seperti database tabel)
2. Unstructured (seperti database non-tabel yang random)
3. Natural Language (Bahasa, perkataan, linguistik)
4. Machine Generated (Diproduksi mesin)
5. Graph Based (Data yang berhubungan satu dengan yg lainnya)
6. Audio, Video, Images 
7. Streaming (data yang mengalir ke sistem)


Proses kerja data sains

1. Membuat sasaran penelitian (apa sasarannya, keuntungan apa, kebutuhan, waktu)
2. Mengambil data
3. Persiapan data (data cleansing, integration dan transformation)
4. Eksplorasi data (membuat pemahaman mendalam ke data tersebut)
5. Memodelkan data (membuat model dengan statistik, machine learning, research dll)
6. Presentasi dan automasi


Tools yang digunakan oleh data saintis

1. Distributed file system (seperti HDFS, Google File System, Red Hat Cluster File System)
2. Distributed programming framework (Apache Spark)
3. Data integration framework (Apache Sqoop)
4. Machine Learning framework (Scikit-learn, NLTK, Pylearn2, TensorFlow)
5. Databases (NoSQL: Neo4j, mongoDB; NewSQL)
6. Tools (Schduling, Bencmarking , Deployment, Service, 


Proses kerja data sains, adalah yang pertama kita membuat sasaran penilitian (why, how dan what) lalu kita mengambil data, mempersiapkan data, mengeksporasi pemahaman kita tentang data tersebut, memodelkan data yang sudah dengan beberapa metode atau senjata yang kita punya. Setelah pemrosesan semua selesai yang terakhir dan paling penting adalah saatnya kita membuat presentasi (mendapatkan jawaban dari kerja pertama) dan mengautomasi data. Proses ini sifatnya fleksibel berarti tidak semua data bisa ditangani dengan cara ini dan tidak semua orang menggunakan cara yang sama. berikut pemrosesan data sains:

1. Membuat sasaran penelitian dan raihan
Disini adalah awal dari penelitian data, kita harus tau apa yang mau kita capai setelah penelitian selesai, kapan penelitian selesai dan bagaimana penelitian kita dapat mempunyai 'impact' yang berarti pada bisnis. Selain itu kita juga harus tau sumber daya apa yang kita punya apa analisis yang kita mau pakai. Banyak data saintis gagal dalam hal ini meskipun mereka brilian dalam matematika dan statistik.

2. Mengambil data
Pengambilan data dapat diambil dari sumber-sumber internal maupun eksternal. Biasanya perusahaan-perusahaan dengan IT professionals mempunya data marts, data warehouses atau data lake yaitu kumpulan-kumpulan data yang mencukupi namun, bila data kurang kita dapat mencari dari sumber lain seperti dari: 
    * data.gov
    * open-data.europa.eu
    * freebase.org
    * data.worldbank.org
    * adidata.org
    * open.fda.gov

3. Persiapan data
Data yang kita ambil harus dipersiapkan terlebih dahulu. Untuk itu, kita melakukan data cleansing yaitu membersihkan dari data-data kotor atau tidak rapih. contoh: data F dan Female, Meter dan Inches, data outlier (yang berbeda dari lainnya yg dapat merusak regresi linier data), data yang tidak mungkin (seperti -1 kelvin), whitespace,  typo dll. Tidak hanya data cleansing, kita juga harus melakukan data combining dari data-data yang jika pada tabel kita dapat melakukan data joining (menggabungkan informasi pada data, ex: menggabungkan informasi jumlah dan letak penjualan), data appending (menambah data yang ada, ex: letak penjualan bulan juni ditambah dengan letak penjualan bulan juli). Kita dapat melakukan teknik 'view' dalam menggabungkan data dengan membuat tabel virtual (bukan menduplikasi data ke tabel baru). Transformasi data juga harus dilakukan dalam pengambilan data agar data mudah dimodelkan, contoh: merubah gender=M/F menjadi M=true/false dan F=true/false.

4. Eksplorasi data
Untuk mendalami pemahaman kita tentang data yang kita punya maka hal yang mudah yang dapat kita lakukan adalah membuat grafis, diagram atau bagan tentang data tersebut. Diagram tersebut dapat menggunakan berbagai macam plot, seperti line plot, bar plot, scatter plot, pie, radial, histogram, boxplot dan plot lainnya. Dengan begitu, kita dapat melihat kecenderungan data, fungsi data, korelasi data, perubahan data dan struktur data. Observasi ini kita lakukan agar nantinya kita mempunya bekal pemahaman yang cukup dalam memodelkan data.
