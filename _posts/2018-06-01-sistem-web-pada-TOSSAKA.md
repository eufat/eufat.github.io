Malam ini aku mau share pengalaman dalam mendesain dan membuat sistem web pada TOSSAKA, salah satu acara terbesar yang ada di fakultas FMIPA UI di. TOSSAKA singkatan dari "Try Out SBMPTN Terpusat Wilayah Jakarta dan Sekitarnya" adalah event tryout tahunan yang dibuat oleh BEM FMIPA UI. Setiap tahun melibatkan 3000-4000 lebih peserta sekolah menengah atas.

![tossaka](https://eufat.github.io/images/tossaka.jpg)
*TOSSAKA Merupakan event try-out tahunan se-jabodetabek*

Menurutku membuat sistem web TOSSAKA adalah pengalaman yang tidak terlupakan. Karena, aku dituntut untuk membuat sistem dari nol sampai digunakan ribuan peserta, sendirian. Awal mulanya, aku diajak oleh teman seangkatanku untuk menjadi web design karena aku memiliki sedikit pengalaman dalam membuat web. Tetapi, aku sendiri mempunyai tekad untuk membuat TOSSAKA menjadi tryout tercanggih yang pernah di selenggarakan di Indonesia, sehingga selama pembuatan sistem ini aku belajar banyak hal mulai dari sisi teknis dan non-teknis. Aku berkesempatan untuk bertanggung jawab dalam membuat sistem web TOSSAKA di tahun 2017 dan 2018, umumnya sistem ini menghabiskan waktu 3-4 bulan untuk dikembangkan secara part-time (aku mengerjakannya sendiri apabila ada waktu kosong saja).

![dashboard-tossaka-1](https://eufat.github.io/images/dashboard-tossaka-1.png)
*Dashboard TOSSAKA 13th di tahun 2017*

![dashboard-tossaka-2](https://eufat.github.io/images/dashboard-tossaka-2.png)
*Dashboard TOSSAKA 14th di tahun 2018*

Sistem web TOSSAKA terdiri dari 4 fitur utama yaitu registrasi, payment, ticket verification dan results. Registrasi adalah sistem untuk pendaftaran peserta, payment adalah fitur untuk pembayaran tryout dan results adalah pengumuman hasil tryout. Ketiga sistem ini saling terintegrasi secara one-way flow yang berarti berurut dari registrasi, lalu payment dan terakhir result. Dari sisi otorisasi sistem hanya dibagi dua saja yaitu admin dan peserta, admin berguna untuk mengatur dan melihat kondisi realtime ketiga fitur tersebut. Untuk stack teknologi aku mengunakan Javascript, React, Redux dan Firebase juga Algolia sebagai search engine.

Untuk sistem registrasi, peserta TOSSAKA di tahun 2018 hanya dapat melakukan pengisian form hanya sekali pada saat signup, tidak bisa diedit atau dirubah. Kenapa didesain seperti ini? karena perubahan pada data peserta memungkinkan terjadinya kesalahpahaman peserta yang mengisi beberapa data peserta pada satu akun seperti beberapa kejadian di tahun 2017 yang menyulitkan admin. Pada pendaftaran juga harus disematkan sistem realtime, yang tersinkronisasi dengan jadwal penutupan pendaftaran. Karena di tahun 2017, admin ticketing, aku dan dua orang teman lainnya kesulitan menghandle ratusan peserta yang overload dikarenakan sistem ini tidak didesain sebelumnya. Mengapa hal ini terjadi? karena kebiasaan orang yang baru sadar apabila sudah dekat waktunya, tidak di antisipasi dari awal. Jadi misal kalau diumumkan pendaftaran akan di tutup pada tanggal 31 pukul 10 PM mereka akan mendaftar pada tanggal 31 pada pukul 9 PM.

Sistem payment atau pembayaran adalah yang paling berat secara teknik web dan mengoperasikannya. Sistem pembayaran pada TOSSAKA memiliki 2 jenis sistem yaitu online dan voucher, online berarti transfer manual ke ATM dan voucher berarti mengisi kode voucher yang dijual secara offline, apabila peserta sudah sukses melakukan pembayaran barulah peserta mendapatkan tiket. Sistem pembayaran online pada event TOSSAKA masih menggunakan verifikasi manual admin, dengan melihat bukti transfer peserta. Sistem ini sangat rentan penipuan dan miss verification (contoh si A tidak mengkonfirmasi pembayaran dan lupa menyimpan bukti) karena itu sebaiknya digunakan payment gateway seperti Midtrans atau Xendit untuk mengotomatisasi pembayaran.

Pada sistem pembayaran voucher terdapat masalah-masalah tersendiri. Seperti contohnya, softcopy voucher TOSSAKA yang di print berkali-kali oleh tim roadshow padahal sebenarnya voucher hanya bisa dipakai sekali dan hangus apabila sudah dipakai. Lucunya, pernah tim dokumentasi di tahun 2017 yang secara tidak sengaja memfoto kode-kode voucher saat roadshow dan disebarkan melalu media sosial. Sehingga, admin harus memblokir beberapa voucher yang terlanjur terekspos kodenya, untuk menghindari pencurian kode voucher (hal ini karena voucher tidak seperti voucher pulsa yang mesti digesek dahulu dengan koin untuk melihat kode).

Ticket verification termasuk hal yang paling krusial pada hari-H karena lambatnya verifikasi oleh panitia dapat mengundur agenda keseluruhan acara. TOSSAKA di tahun 2017, menggunakan verifikasi manual dengan data registrasi dan payment yang dieksport di Google Sheets sehingga panitia dapat memverifikasi apabila tiket sesuai dengan data yang ada, lalu apabila data sesuai panitia akan klik "Attend" pada web. Cara kerja ini sangatlah lambat, sehingga verifikasi tiket memakan waktu dengan antrian peserta yang sangat-sangat panjang. TOSSAKA di tahun 2018, aku mencoba melakukan approach yang berbeda, kali ini aku mendesain tiket dengan QR Code lalu panitia akan menscan tiket tersebut seperti di cashier. Ternyata secara tidak diduga sistem ini jauh lebih cepat dan hemat man-power, sebagai perbandingan di TOSSAKA 13th (2017) verifikasi tiket memakan waktu 3 jam dengan lebih dari 20 panitia yang memverifikasi, di TOSSAKA 14th (2018) hanya memakan waktu 30 menit dengan jumlah panitia yang kurang lebih 10 orang. Artinya sistem ini mempercepat waktu verifikasi hingga 12x lipat dari sebelumnya!, antrian peserta pun juga terbilang pendek.

![scan-ticket-1](https://eufat.github.io/images/scan-ticket-1.png)
*Sistem Scanning Ticket mempercepat verifikasi sampai 12x lipat*

Pengumuman nilai, momen ini adalah momen yang paling ditunggu-tunggu peserta. Di tahun 2017 aku dapat membuat sistem results yang sangat baik, karena data hasil scan yang terstruktur, rapih dan lengkap sehingga peserta yang tidak mendapatkan nilai terbilang sangat sedikit. Di tahun 2018 ternyata hasil scan dari vendor yang berbeda (tahun sebelumnya staedtler) jauh dari harapan, sehingga pengumuman di web tidak dapat dilakukan (data peserta terurut dengan excel). Untuk mengolah data peserta dan menghasilkan urutan nilai terbaik aku membuat script Python dan library Pandas.

Berikut merupakan alur-alur pada sistem web TOSSAKA.

![sistem-web-tossaka-ticketing-1](https://eufat.github.io/images/sistem-web-tossaka-ticketing-1.png)
*Alur pembelian tiket dengan voucher*

![sistem-web-tossaka-ticketing-2](https://eufat.github.io/images/sistem-web-tossaka-ticketing-2.png)
*Alur pembelian tiket dengan transfer manual*

![sistem-web-tossaka-ticketing-3](https://eufat.github.io/images/sistem-web-tossaka-ticketing-3.png)
*Alur pembelian tiket grup*


TOSSAKA adalah acara yang dibuat oleh mahasiswa sains, jadi seharusnya data dan fakta adalah hal yang menjadi acuan pertama dalam membuat keputusan. Analisis data untuk melakukan data-driven decision agar market targeting, penutupan pendaftaran, pembukaan pendaftaran, tempat roadshow menjadi salah satu kaidah penting untuk menjalankan event agar sukses dan efisien. Berikut merupakan sebagian kecil data-data yang diliput dari acara TOSSAKA 2017 dan 2018.

![data-tossaka-1](https://eufat.github.io/images/data-tossaka-1.png =200x)
*Statistik user dan session di TOSSAKA tahun 2017*

![data-tossaka-2](https://eufat.github.io/images/data-tossaka-2.png =200x)
*Statistik user dan session di TOSSAKA tahun 2018*

![data-tossaka-3](https://eufat.github.io/images/data-tossaka-3.png =200x)
*Distribusi device yang digunakan untuk mengakses web TOSSAKA tahun 2017 dan 2018*

![data-tossaka-4](https://eufat.github.io/images/data-tossaka-4.png =200x)
*Domisili peserta TOSSAKA tahun 2017*

![data-tossaka-5](https://eufat.github.io/images/data-tossaka-5.png =200x)
*Distribusi tipe ujian IPA vs IPS*

All in all, TOSSAKA merupakan event yang cukup besar dan untuk membuat event berjalan lancar dan sukses dibutuhkan kerja keras. Manfaat dari tryout adalah mendidik adik-adik yang masih duduk di bangku SMA untuk memotivasi mereka lebih giat belajar, lebih cerdas dan nantinya memberikan menjadi manusia yang lebih berkualitas. Untuk aku pribadi membuat sistem web TOSSAKA adalah sebuah kesenangan dan kebanggaan tersendiri, karena sudah digunakan 9 ribu orang lebih dan menghasilkan gross revenue lebih dari 280 juta rupiah.

Terimakasih sudah membaca.



