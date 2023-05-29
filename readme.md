## Nama      : Muhammad Hamamiy Zadah
## Kelas     : TI - 3C
## No. Absen : 12
##

### Kode 1 
[ sys.argv, sys.stderr, StreamingContext, sc, socketTextStream, reduceByKey, lambda line, awaitTermination ]
- sys.argv :  Sintaks sys.argv adalah sebuah list yang berisi argumen baris perintah yang diberikan saat menjalankan program Python dari terminal. 

- sys.stderr :  sys.stderr adalah sebuah objek aliran (stream) yang digunakan untuk menampilkan pesan kesalahan (error) pada konsol.   dapat menggunakan sys.stderr.write() untuk menuliskan pesan kesalahan ke stderr.

- StreamingContext : StreamingContext adalah kelas inti dalam Spark Streaming. Ini adalah entitas utama yang digunakan untuk mengonfigurasi aplikasi Spark Streaming.

- sc : sc adalah objek SparkContext yang digunakan untuk berinteraksi dengan Apache Spark cluster. Ini adalah objek yang dibutuhkan untuk memulai aplikasi Spark dan mengakses fungsionalitas Spark. Dalam konteks Spark Streaming, sc digunakan untuk membuat objek StreamingContext yang kemudian digunakan untuk mengonfigurasi dan menjalankan alur kerja Spark Streaming.


- socketTextStream : socketTextStream adalah metode dalam objek StreamingContext yang digunakan untuk membuat DStream (Discretized Stream) dari data streaming yang masuk melalui koneksi socket.   dapat menentukan alamat IP dan port untuk mendengarkan data streaming. Misalnya, socketTextStream("localhost", 9999) akan membuat DStream yang mengambil data streaming dari localhost pada port 9999.

- reduceByKey : reduceByKey adalah operasi transformasi dalam Spark Streaming yang mengelompokkan pasangan kunci-nilai (key-value pairs) berdasarkan kunci dan kemudian mengurangi nilai-nilai yang terkait dengan kunci yang sama menggunakan fungsi pengurangan (reducing function). Hasilnya adalah DStream baru dengan pasangan kunci-nilai yang telah diurutkan dan di-reduce berdasarkan kunci.

- lambda line : lambda line adalah sintaks untuk membuat fungsi lambda (fungsi tanpa nama) yang mengambil argumen line. Fungsi lambda ini sering digunakan dalam pemrograman Spark Streaming untuk melakukan operasi pemetaan pada setiap elemen DStream.

- awaitTermination : awaitTermination adalah metode dalam objek StreamingContext yang memulai proses pemrosesan data streaming dan memblokir eksekusi sampai streaming context berhenti secara manual atau karena terjadi kesalahan. Metode ini digunakan untuk menjaga agar aplikasi Spark Streaming tetap berjalan sampai diberikan sinyal untuk berhenti.
##

### Kode 2
[ nc, lk ]
- nc : nc (netcat) untuk menyediakan sumber data streaming melalui koneksi socket.

- lk

##


### Kode 3
[ spark-submit, master, local[*] ]
- spark-submit : spark-submit adalah perintah yang digunakan untuk mengirimkan aplikasi Spark kepada cluster Spark untuk dieksekusi. Perintah ini digunakan untuk memulai aplikasi Spark yang sudah dikompilasi dan memasukkan aplikasi tersebut ke dalam cluster Spark yang terpisah.

- master : master adalah parameter yang digunakan dalam perintah spark-submit untuk menentukan URL atau mode koneksi ke Spark master. Spark master adalah komponen utama dalam arsitektur cluster Spark yang bertanggung jawab untuk mengelola sumber daya cluster dan mendistribusikan tugas pemrosesan ke node-node worker.

- local[*] : local[*] adalah salah satu nilai yang dapat   berikan sebagai argumen master dalam spark-submit. Nilai ini mengindikasikan bahwa aplikasi Spark akan dijalankan dalam mode lokal menggunakan semua core CPU yang tersedia. Dalam hal ini, Spark akan berjalan dalam satu JVM (Java Virtual Machine) dan tidak memerlukan cluster Spark yang terpisah.

##


### Kode 4 
[ ssc.checkpoint, parallelize, updateStateByKey, flatMap ]
- ssc.checkpoint : ssc.checkpoint adalah metode dalam objek StreamingContext yang digunakan untuk mengatur lokasi penyimpanan checkpoint dalam Spark Streaming. Checkpoint adalah mekanisme yang digunakan untuk menyimpan status streaming kontinu dan metadata dalam proses pemrosesan data streaming. Dengan mengatur checkpoint, dapat memastikan toleransi kesalahan dan pemulihan yang lebih baik dalam Spark 

- parallelize : parallelize adalah metode dalam objek SparkContext yang digunakan untuk membuat RDD (Resilient Distributed Dataset) dari kumpulan data yang ada di memori. Metode ini membagi data menjadi bagian-bagian yang terdistribusi di seluruh node dalam cluster Spark.

- updateStateByKey : updateStateByKey adalah operasi transformasi dalam Spark Streaming yang digunakan untuk menggabungkan data streaming yang baru dengan data sebelumnya berdasarkan kunci yang sama. Operasi ini memungkinkan untuk mempertahankan status (state) yang dapat diperbarui dari waktu ke waktu saat data streaming masuk

- flatMap : flatMap adalah operasi transformasi dalam Spark yang diterapkan pada RDD atau DStream untuk menghasilkan elemen baru dengan mengaplikasikan fungsi ke setiap elemen sumber dan kemudian menggabungkan hasilnya menjadi satu. Operasi flatMap mirip dengan map, tetapi dengan kemampuan untuk menghasilkan nol, satu, atau banyak elemen baru dari setiap elemen sumber.

##

### Kode 5 
[ rrd.take(5), transform, rdd.sortByKey(False) ]
- rrd.take(5) : rdd.take(5): rdd.take(5) adalah metode dalam RDD (Resilient Distributed Dataset) yang digunakan untuk mengambil beberapa elemen pertama dari RDD. Dalam contoh ini, 5 menunjukkan jumlah elemen yang ingin diambil dari RDD. Metode ini mengembalikan array yang berisi elemen-elemen tersebut. Misalnya, jika   memiliki RDD yang berisi [1, 2, 3, 4, 5, 6, 7, 8, 9, 10], rdd.take(5) akan mengembalikan [1, 2, 3, 4, 5], yaitu lima elemen pertama dari RDD.

- transform : adalah metode dalam DStream (Discretized Stream) yang digunakan untuk mengubah setiap batch DStream dengan menerapkan fungsi transformasi tertentu. Metode ini memungkinkan  untuk memanipulasi setiap batch DStream secara independen. Fungsi transformasi yang diberikan akan diaplikasikan pada setiap batch DStream secara paralel. Misalnya, jika   memiliki DStream dan   ingin mengubah setiap elemennya dengan fungsi tertentu, dapat menggunakan transform untuk menerapkan fungsi tersebut pada setiap batch DStream.

- rdd.sortByKey(False) : rdd.sortByKey(False) adalah metode dalam RDD yang digunakan untuk mengurutkan elemen-elemen RDD berdasarkan kunci (jika RDD berisi pasangan kunci-nilai). False yang diberikan sebagai argumen menunjukkan bahwa pengurutan akan dilakukan secara menurun (descending order). Jika ingin pengurutan dilakukan secara naik (ascending order), dapat menggunakan True sebagai argumen. Metode ini menghasilkan RDD baru yang berisi elemen-elemen yang diurutkan berdasarkan kunci. Misalnya, jika    memiliki RDD dengan pasangan kunci-nilai seperti [("b", 2), ("a", 1), ("c", 3)], rdd.sortByKey(False) akan menghasilkan RDD baru dengan urutan [("c", 3), ("b", 2), ("a", 1)].

##