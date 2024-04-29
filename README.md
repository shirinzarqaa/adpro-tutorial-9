### Refleksi

#### What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?

- **Unary RPC**: Metode ini melibatkan klien mengirimkan satu permintaan ke server dan menunggu satu respons. Cocok digunakan saat klien hanya perlu mengirimkan permintaan sekali dan menerima respons tunggal.
- **Server Streaming RPC**: Dalam metode ini, klien mengirimkan satu permintaan ke server dan menerima respons yang berkelanjutan dalam bentuk stream. Cocok digunakan saat klien memerlukan respon yang berkelanjutan dari server.
- **Bidirectional Streaming RPC**: Metode ini memungkinkan klien dan server untuk saling mengirimkan sejumlah permintaan dan respons melalui satu koneksi yang berkelanjutan. Cocok digunakan saat interaksi antara klien dan server bersifat asinkron dan memerlukan pengiriman data dua arah secara real-time.

#### What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?

- **Autentikasi**: Penting untuk memastikan bahwa hanya klien yang sah yang dapat terhubung ke layanan gRPC. Hal ini bisa dicapai melalui metode autentikasi seperti token atau sertifikat.
- **Otorisasi**: Perlu diterapkan aturan akses yang ketat untuk menentukan akses mana yang diberikan kepada klien setelah berhasil terautentikasi.
- **Enkripsi Data**: Semua data yang dikirimkan antara klien dan server harus dienkripsi untuk mencegah penyadapan atau modifikasi data oleh pihak yang tidak berwenang.

#### What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?

- **Sinkronisasi**: Perlu memastikan sinkronisasi antara pengiriman permintaan dan respons dari klien dan server untuk menghindari deadlock atau masalah sinkronisasi lainnya.
- **Manajemen Memori**: Dalam situasi streaming yang intensif, perlu memperhatikan manajemen memori untuk mencegah kebocoran memori atau konsumsi memori yang berlebihan.

#### What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?

- **Kelebihan**:
  - Mudah digunakan dan diintegrasikan dengan infrastruktur tokio.
  - Memberikan abstraksi yang nyaman untuk mengelola aliran data.
  - 
- **Kekurangan**:
  - Tidak sefleksibel dalam mengelola sinyal khusus atau error dari stream.
  - Mungkin memerlukan perhatian ekstra dalam manajemen memori jika digunakan dalam situasi streaming yang intensif.

#### In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?
- **Penggunaan Modul**: Memisahkan fungsi-fungsi terkait menjadi modul-modul terpisah untuk memfasilitasi penggunaan ulang dan meningkatkan kejelasan kode.
- **Penggunaan Trait**: Menerapkan trait untuk operasi-operasi umum seperti autentikasi atau otorisasi, sehingga dapat dengan mudah digunakan oleh berbagai bagian dari kode.

#### In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?

- **Validasi Data**: Melakukan validasi data yang lebih ketat untuk memastikan data yang diterima dari klien sesuai dengan aturan bisnis dan keamanan yang ditetapkan.
- **Manajemen Kesalahan**: Mengelola kasus-kasus kesalahan yang lebih kompleks, seperti kegagalan pembayaran, pemrosesan ulang transaksi, atau penanganan konflik transaksi.

#### What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?

- **Interoperabilitas**: Memungkinkan komunikasi yang efisien dan terstruktur antara layanan-layanan yang ditulis dalam berbagai bahasa pemrograman dan menjalankan di platform yang berbeda.
- **Performa**: HTTP/2, yang digunakan sebagai protokol dasar gRPC, memiliki kemampuan multiplexing dan kompresi yang dapat meningkatkan kinerja aplikasi terdistribusi.
- **Pembangunan dan Pemeliharaan**: Memerlukan peralatan pengembangan dan pemeliharaan yang berbeda dibandingkan dengan pendekatan tradisional seperti REST API.

#### What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?
- **Kelebihan HTTP/2**:
  - Kemampuan multiplexing dan kompresi data yang meningkatkan kinerja aplikasi.
  - Dukungan untuk streaming data dalam satu koneksi.
- **Kekurangan HTTP/2**:
  - Kompleksitas implementasi yang lebih tinggi.
  - Dibutuhkan dukungan server dan klien yang kompatibel.

#### How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?
- **API REST**: Biasanya mengikuti model permintaan-respons, di mana klien membuat permintaan ke server dan menunggu respons tunggal. Tidak cocok untuk komunikasi real-time.
- **gRPC**: Memungkinkan streaming dua arah, yang memungkinkan klien dan server untuk berinteraksi secara real-time dan meresponsif.

#### What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?
- **gRPC dengan Protocol Buffers**: Menawarkan struktur data yang didefinisikan secara ketat dan interoperabilitas yang baik antara layanan-layanan yang berbeda, tetapi kurang fleksibel dalam hal pengembangan dan evolusi skema.
- **JSON dalam API REST**: Memiliki fleksibilitas yang lebih besar dalam hal struktur dan evolusi data, tetapi dapat menghadapi tantangan dalam hal interoperabilitas dan validasi data yang lebih lemah.