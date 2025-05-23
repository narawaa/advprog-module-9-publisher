Pemrograman Lanjut (Advanced Programming) 2024/2025 Genap

- Nama : Nashwa Ghania
- NPM : 2306241770
- Kelas : Pemrograman Lanjut - A

### Reflection:
#### 1. How much data your publisher program will send to the message broker in one run?
Dalam sekali dijalankan, program publisher ini akan mengirimkan 5 pesan ke message broker. Setiap pesan adalah instance dari UserCreatedEventMessage yang berisi dua string: user_id dan user_name. Karena semua data bersifat teks dan pendek (misalnya user_id: "1" dan user_name: "2306241770-Amir"), total data yang dikirim secara kumulatif tergolong kecil, hanya beberapa ratus byte dalam satu kali run. Namun, ukuran sebenarnya yang dikirim tergantung pada serialisasi menggunakan format Borsh, yang dikenal efisien dan ringan.

#### 2. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?
URL amqp://guest:guest@localhost:5672 yang digunakan di program publisher sama dengan yang ada di program subscriber. Ini berarti bahwa keduanya terhubung ke message broker yang sama, yaitu RabbitMQ atau sistem AMQP lain yang berjalan secara lokal pada port 5672. Username dan password guest digunakan sebagai kredensial autentikasi default. Dengan koneksi yang sama ini, pesan yang diterbitkan oleh publisher dapat langsung diterima oleh subscriber yang mendengarkan topik atau routing key yang sesuai.

#### Running RabbitMQ
![image](images/result-1.png)

#### Sending and processing event
![image2](images/result-2.png)
![image3](images/result-3.png)

Publisher dan subscriber sama-sama terhubung ke server RabbitMQ yang sama. Jadi, setiap kali publisher mengirimkan data, subscriber akan langsung menerima pesan tersebut.

#### Monitoring chart based on publisher
![image4](images/result-4.png)

Saat publisher dijalankan, jumlah pesan yang dikirim ke message broker meningkat. Lonjakan (spike) ini menunjukkan adanya peningkatan tiba-tiba dalam kecepatan pengiriman pesan dari publisher ke broker, yang kemudian diteruskan ke subscriber.