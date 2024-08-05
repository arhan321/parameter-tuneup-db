# Tune Up Database MariaDB

### Penjelasan Pengaturan

- **max_connections**: Menentukan jumlah maksimum koneksi simultan yang diperbolehkan. Dengan pengaturan `10000`, server dapat menangani hingga 10.000 koneksi simultan. Ini berguna untuk aplikasi dengan banyak pengguna atau koneksi simultan.

- **connect_timeout**: Waktu tunggu (dalam detik) untuk koneksi baru sebelum server membatalkan koneksi. Pengaturan `5` detik memastikan koneksi yang lambat akan segera ditolak, mengurangi beban pada server.

- **wait_timeout**: Waktu (dalam detik) koneksi dapat tetap idle sebelum ditutup oleh server. Pengaturan `300` detik membantu mengurangi penggunaan sumber daya oleh koneksi yang tidak aktif.

- **interactive_timeout**: Waktu (dalam detik) untuk koneksi interaktif tetap idle sebelum ditutup. Pengaturan `300` detik ini memastikan bahwa koneksi interaktif yang tidak aktif akan segera ditutup.

- **max_allowed_packet**: Ukuran maksimum dari satu paket data yang dikirim atau diterima. Dengan pengaturan `512M`, server dapat menangani kueri atau data besar.

- **thread_cache_size**: Menentukan jumlah thread yang disimpan dalam cache untuk digunakan kembali. Pengaturan `2048` mengurangi overhead yang terkait dengan pembuatan thread baru.

- **sort_buffer_size**: Ukuran buffer yang digunakan untuk operasi pengurutan. Dengan pengaturan `64M`, ini memungkinkan operasi pengurutan yang lebih cepat dan lebih efisien.

- **bulk_insert_buffer_size**: Ukuran buffer yang digunakan untuk operasi bulk insert. Dengan pengaturan `1G`, ini memungkinkan penyisipan data dalam jumlah besar lebih cepat.

- **tmp_table_size**: Ukuran maksimum tabel sementara dalam memori. Pengaturan `2G` mengizinkan tabel sementara besar dibuat di memori sebelum dialihkan ke disk.

- **max_heap_table_size**: Ukuran maksimum tabel HEAP dalam memori. Pengaturan `2G` memastikan bahwa tabel HEAP dapat berukuran besar.

- **join_buffer_size**: Ukuran buffer yang digunakan untuk operasi join. Pengaturan `64M` mengizinkan join yang lebih kompleks dan besar dilakukan dengan lebih efisien.

- **query_cache_limit**: Ukuran maksimum hasil query yang dapat disimpan dalam query cache. Dengan pengaturan `8M`, hasil query kecil dapat disimpan dan diakses dengan cepat.

- **query_cache_size**: Total ukuran memori yang dialokasikan untuk query cache. Dengan pengaturan `1G`, ini memungkinkan lebih banyak hasil query disimpan dalam cache.

- **query_cache_type**: Menentukan kapan query cache diaktifkan. Pengaturan `1` mengaktifkan query cache secara umum.

- **key_buffer_size**: Ukuran buffer yang digunakan untuk indeks MyISAM. Pengaturan `2G` memungkinkan penyimpanan indeks besar dalam memori.

- **table_open_cache**: Jumlah maksimum tabel yang dapat dibuka secara bersamaan. Dengan pengaturan `8000`, ini meningkatkan jumlah tabel yang dapat dibuka tanpa harus menutup yang lain.

- **myisam_sort_buffer_size**: Ukuran buffer yang digunakan untuk mengurutkan indeks MyISAM selama operasi REPAIR TABLE atau CREATE INDEX. Dengan pengaturan `8G`, ini memungkinkan operasi pengurutan yang sangat besar dilakukan dengan cepat.

- **read_buffer_size**: Ukuran buffer yang digunakan untuk operasi baca MyISAM. Pengaturan `32M` memungkinkan operasi baca besar dilakukan dengan lebih efisien.

- **read_rnd_buffer_size**: Ukuran buffer yang digunakan untuk operasi baca acak MyISAM. Pengaturan `64M` meningkatkan efisiensi operasi baca acak.

- **log_error**: Lokasi file log kesalahan. Pengaturan ini memastikan bahwa semua kesalahan dicatat untuk analisis lebih lanjut.

- **slow_query_log**: Mengaktifkan pencatatan query lambat. Pengaturan `1` mengaktifkan log query lambat.

- **slow_query_log_file**: Lokasi file log query lambat. Pengaturan ini memastikan bahwa query yang memakan waktu lama dicatat.

- **long_query_time**: Waktu (dalam detik) yang menentukan batas untuk query lambat. Pengaturan `0.1` detik memastikan bahwa query yang memakan waktu lebih dari `0.1` detik dicatat.

- **log_bin**: Lokasi file log biner untuk replikasi. Pengaturan ini memastikan bahwa perubahan dicatat untuk replikasi atau pemulihan.

- **expire_logs_days**: Jumlah hari log biner disimpan sebelum dihapus. Pengaturan `10` hari membantu mengelola ukuran log biner.

- **max_binlog_size**: Ukuran maksimum log biner sebelum berputar. Pengaturan `1G` memastikan bahwa log biner tidak tumbuh terlalu besar.

- **default_storage_engine**: Mesin penyimpanan default. Pengaturan ini memastikan bahwa InnoDB digunakan sebagai mesin penyimpanan default.

- **innodb_buffer_pool_size**: Ukuran buffer pool InnoDB. Pengaturan `64G` (70-80% dari total RAM) memungkinkan penyimpanan data dan indeks dalam memori untuk akses cepat.

- **innodb_log_file_size**: Ukuran file log InnoDB. Pengaturan `16G` memungkinkan pencatatan transaksi besar tanpa sering berputar.

- **innodb_log_buffer_size**: Ukuran buffer log InnoDB. Pengaturan `2G` memungkinkan penyimpanan lebih banyak log dalam memori sebelum disimpan ke disk.

- **innodb_file_per_table**: Mengaktifkan penggunaan file tablespace per tabel. Pengaturan ini memastikan bahwa setiap tabel memiliki file tablespace sendiri.

- **innodb_flush_method**: Metode flush untuk InnoDB. Pengaturan `O_DIRECT` mengurangi beban sistem file cache.

- **innodb_flush_log_at_trx_commit**: Mengontrol kapan log transaksi InnoDB diflush ke disk. Pengaturan `2` meningkatkan kinerja dengan risiko kehilangan data minimal dalam kasus crash.

- **innodb_thread_concurrency**: Jumlah maksimum thread yang dapat digunakan InnoDB secara bersamaan. Pengaturan `128` memungkinkan lebih banyak thread paralel.

- **innodb_read_io_threads**: Jumlah thread I/O baca InnoDB. Pengaturan `64` meningkatkan performa baca paralel.

- **innodb_write_io_threads**: Jumlah thread I/O tulis InnoDB. Pengaturan `64` meningkatkan performa tulis paralel.

- **innodb_io_capacity**: Kapasitas I/O maksimum yang dapat digunakan InnoDB. Pengaturan `16000` memastikan bahwa InnoDB dapat memanfaatkan I/O disk yang tinggi.

- **innodb_io_capacity_max**: Kapasitas I/O maksimum dalam situasi ekstrem. Pengaturan `32000` memastikan bahwa InnoDB dapat memanfaatkan I/O disk maksimal dalam situasi beban tinggi.

- **innodb_buffer_pool_instances**: Jumlah instance buffer pool InnoDB. Pengaturan `64` membagi buffer pool menjadi beberapa instance untuk meningkatkan performa pada sistem multi-core.

- **innodb_purge_threads**: Jumlah thread untuk pembersihan log InnoDB. Pengaturan `16` meningkatkan performa pembersihan.

- **innodb_page_cleaners**: Jumlah thread untuk membersihkan halaman InnoDB. Pengaturan `16` memastikan bahwa halaman yang dimodifikasi dibersihkan dengan cepat.
