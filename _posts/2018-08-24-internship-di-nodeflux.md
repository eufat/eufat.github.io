Pada liburan semester enam ke tujuh, aku diwajibkan mengambil kerja lapangan. Umumnya dari teman-teman di peminatanku di instrumentasi mengambil kerja praktek di LIPI, BPPT, dan BATAN, institusi riset negara. Namun, aku ingin mencari pengalaman di perusahaan-perusahaan  teknologi yang bergelut di bidang Computer Vision. Karena, nantinya skripsiku akan diarahkan kesana dan ada salah satu projectku yang sudah didanai DIIB UI dan RISTEKDIKTI yang berurusan dengan Computer Vision. Jadi kalau skripsi, internship dan project bisa satu arah, kenapa tidak?

Awalnya aku meng-apply internship ke beberapa perusahaan di Malaysia dan Singapura karena ingin mencoba bekerja di luar Indonesia dan sekalian memupuk tabungan hehehe, aku sudah coba apply ke Intel di Penang Malaysia, [Visenze](https://www.visenze.com/) di Singapura dan [nuTonomy](https://www.nutonomy.com/) juga di Singapura. Tapi, sayangnya di Intel Malaysia aku di tolak (kemungkinan karena orang Indonesia), Visenze di undur internshipnya dan nuTonomy tidak ada kabar. Sedihkan banget kan, hahaha.

Tapi, ternyata setelah browsing-browsing ada loh satu startup di Indonesia yang fokusnya di Computer Vision, nama startupnya [Nodeflux](https://nodeflux.io/). Nodeflux itu adalah startup mempunyai produk IVA (Intelligent Video Analytics) jadi dengan Nodeflux kita bisa menganalisis konten pada video dengan kamera CCTV sebagai instrumennya. Uniknya, Nodeflux adalah satu-satunya perusahaan di Indonesia yang bergelut di IVA. Nodeflux juga satu-satunya startup di Indonesia yang ikut di akselerator [NVIDIA Inception](https://www.nvidia.com/en-us/deep-learning-ai/startups/), akselerator yang mendukung startup dengan teknologi kecerdasan buatan (AI) dan Deep Learning. Kalo dilihat dari websitenya Nodeflux [disini](https://nodeflux.io/), salah satu client mereka itu BIN (Badan Intelijen Negara) mirip CIA, keren banget kan?

Setelah apply di Nodeflux ada technical assignment (TA) dan diberi waktu 2 hari untuk menyelesaikannya, ada 14 soal cuma yang aku bisa kerjain 10 soal saja, solusi yang aku submit ada [disini](https://github.com/eufat/nodeflux-ta). TA nya relatif mudah tapi broad banget pertanyaannya, aku bisa kerjaiin beberapa soal web karena sudah sering web development dan pernah internship di startup SaaS sebelumnya. Tapi sebenarnya, kita ndak usah kerjaiin semuanya, karena yang di nilai approach dari solusinya. Gak lama setelah TA, ada interview online dan akhirnya aku lolos dan diterima internship disana, hore.

Kantor Nodeflux ada di Kemang, kantornya di rumah yang tergolong besar dan ada kolam renangnya loh. Internship disana pakaiannya casual jadi ga ribet, aku suka banget yang begini. Ada dapurnya pula, jadi bisa masak-masak, malah sering juga kita dikasih makanan dan cemilan cuma-cuma hahaha. Karena lokasinya di Kemang jadi relatif jauh dari kampus UI, sekitar 1 jam pergi kesana dengan bikun, kereta dan Grab. Aku pergi internship biasanya jam 9.30 sampai disana jam 10.30-11.00. Biasanya, aku yang paling terlambat dari anak-anak intern yang lain hahaha. Ada alasannya, karena kalau pergi jam 8.00 naik KRL itu mirip truk kambing kurban, dempet-dempetan, panas dan bau. Pokoknya ndak manusiawi lah, sampai kantor udah ga mood.

Selama internship aku dan anak-anak intern lainny (dari UI dan ITB) buat macam-macam. Di awal-awal kami membuat sistem untuk benchmarking message broker seperti RabbitMQ, Redis, NSQ dan Apache Kafka untuk transmisi frame gambar pada video. Disini aku bertugas untuk mengolah dan memvisualisasi data dengan [ELK stack](https://www.elastic.co/elk-stack) (Elasticsearch, Logstash dan Kibana) untuk nantinya di analisa sistem mana yang paling efisien resource, cepat dan reliable. Yang paling menantang adalah pada konfigurasi Logstash yang berguna untuk memfilter dan memproses data sebelum diterima Elasticsearch.

Di pertengahan internship kami menggabungkan message broker, object detector, dan streamer untuk melihat benchmark sistem secara end-to-end, di tugas ini aku bertugas untuk membuat object detector dengan pretrained model dan membuat sistem streaming gambar sederhana dengan WebSocket. Aku juga sempat mempelajari beberapa arsitektur model Deep Learning untuk real-time object detection seperti [MobileNet](https://arxiv.org/abs/1704.04861) dan [YOLO](https://arxiv.org/abs/1506.02640).

Lalu, di akhir internship tugasku mencoba berbagai metode streaming menggunakan protokol yang berbeda-beda seperti RTP/RTSP, DASH dan WebRTC. Dari tiga protokol itu yang paling sulit di implementasi adalah WebRTC, karena untuk kebutuhan Nodeflux pada streaming yang arahnya server-to-client berbeda dengan komunikasi umum yang digunakan WebRTC, yaitu komunikasi realtime peer-to-peer atau client-to-client. Selain itu, minimnya library yang mature dan examples menjadi kesulitan tersendiri. Di sela-sela tiga project utama tadi, aku juga menyempatkan untuk membuat dua internal tool sederhana, yaitu aplikasi React dan CLI Python untuk membantu engineer Nodeflux dalam memvalidasi dan meng-gather data.

Ada perks-perks dan momen unik selama internship. Untuk eksperimentasi, beberapa virtual machine disewakan khusus untuk anak-anak intern, bahkan salah satu virtual machine tersebut ada yang ditenagai oleh [NVIDIA V100](https://www.nvidia.com/en-us/data-center/tesla-v100/) (GPU untuk datacenter paling cepat sampai saat ini). Pada saat internship Nodeflux juga pernah diliput MetroTV, jadi lucu aja lagi programming di sampingnya ada cameraman, kan jadi grogi hahaha. Saat Agustusan ada lomba-lomba di Nodeflux, banyak hadiahnya lagi dan akhirnya kolam renang di Nodeflux dipakai hahaha. Tapi sayangnya, aku tidak ikut karena ada urusan di kampus.

Overall, internship di Nodeflux itu keren dan menantang tapi tetap seru dan santai.




